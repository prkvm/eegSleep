import os
import csv
import math
import copy
import numpy as np
import pandas as pd
import seaborn as sns


def csvToVec(fname):
    arr = []
    with open(fname, 'r', newline='') as csvfile:
        spamreader = csv.reader(csvfile, delimiter=';', quotechar=' ')
        for row in spamreader:
            r = list(map(float, row))
            arr.append(r[0])
            arr.append(r[1])
    return (arr)


def measureEuqlid(v1, v2):
    dist = 0
    for i in range(0, min(len(v1), len(v2))):
        dist += (v1[i]-v2[i])**2
    return (math.sqrt(dist))


# k11 = MeasureEuqlid(csv2vec('C:\Programming\kash 1_A1.csv'),
#                     csv2vec('C:\Programming\kash 2_A1.csv'))
# print(k11)

# k12 = MeasureEuqlid(csv2vec('C:\Programming\kash 1_A1.csv'),
#                     csv2vec('C:\Programming\\noga 1_A1.csv'))
# print(k12)

# k13 = MeasureEuqlid(csv2vec('C:\Programming\kash 2_A1.csv'),
#                     csv2vec('C:\Programming\\noga 1_A1.csv'))
# print(k13)
# k14 = MeasureEuqlid(csv2vec('C:\Programming\\ruka 1_A1.csv'),
#                     csv2vec('C:\Programming\\ruka 2_A1.csv'))
# print(k14)


def getSrVec(listVec):
    m = len(listVec[0])
    for vec in listVec:
        if (len(vec) < m):
            m = len(vec)
    srVec = [0]*m
    for i in range(m):
        for vec in listVec:
            srVec[i] += vec[i]
        srVec[i] /= len(listVec)
    return (srVec)


def getListVecs(directory):
    files = list(filter(lambda x: x.endswith('.csv'), os.listdir(directory)))
    listVec = list(map(lambda x: csvToVec(directory+'\\'+x), files))
    return getSrVec(listVec)


dataset = [getListVecs('C:\Programming\py\EEGsleep\dataset\golova'),
           getListVecs('C:\Programming\py\EEGsleep\dataset\kashel'),
           getListVecs('C:\Programming\py\EEGsleep\dataset\korpus'),
           getListVecs('C:\Programming\py\EEGsleep\dataset\\noga'),
           getListVecs("C:\Programming\py\EEGsleep\dataset\\ruka")
           ]


def main(vec, lstvec, param):
    return list(map(lambda x: param(vec, x), lstvec))


print(main(csvToVec('C:\Programming\kash 1_A1.csv'), dataset, measureEuqlid))
