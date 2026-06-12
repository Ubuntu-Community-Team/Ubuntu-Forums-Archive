---
title: "Why the tons of scim processes?"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tnunamak on 2008-10-01
This doesn't seem to be right...

```

tnunamak@tnunamak-desktop:~$ ps aux | grep scim
tnunamak  5541  0.0  0.0   3236   792 pts/2    S+   13:04   0:00 grep scim
tnunamak  8097  0.0  0.0   4504   748 ?        Ss   Sep30   0:01 /usr/lib/scim-1.0/scim-launcher -d -c simple -e all -f socket --no-stay -d
tnunamak  8099  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8103  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8107  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8111  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8115  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8119  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8123  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8127  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8131  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8135  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8145  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8149  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8153  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8157  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8161  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8165  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8169  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8173  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8177  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8181  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8245  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8247  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8249  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8251  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8253  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8255  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8257  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8259  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8261  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8277  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8300  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8305  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8311  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8318  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8327  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8338  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8345  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8349  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8353  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8781  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8785  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8789  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8793  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8797  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8801  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8805  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8809  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8813  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8817  0.0  0.1  43244  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8827  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8831  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8835  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8839  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8843  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8847  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8851  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8855  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8859  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8863  0.0  0.1  43132  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8911  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8917  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8921  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8925  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8929  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8933  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8937  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8941  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8945  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8949  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8964  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8971  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8983  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8987  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8991  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8995  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  8999  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9003  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9007  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9012  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9053  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9057  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9079  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9090  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9094  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9098  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9102  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9106  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9110  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9118  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9130  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9136  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9140  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9144  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9148  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9152  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9156  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9160  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9164  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9168  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9278  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9284  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9288  0.0  0.1  43264  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9292  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9296  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9300  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9309  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9313  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9317  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9321  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9585  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9589  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9593  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9597  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9599  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9601  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9606  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9615  0.0  0.1  43164  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9617  0.0  0.1  43164  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9626  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9640  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9644  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9648  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9652  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9656  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9660  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9666  0.0  0.1  43276  3628 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak  9971  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9978  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9982  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak  9986  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10015  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10047  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10110  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10163  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10167  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10171  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10179  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10183  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10187  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10191  0.0  0.1  43160  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10195  0.0  0.1  43160  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10199  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10203  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10207  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10211  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10215  0.0  0.1  43280  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10355  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10359  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10363  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10367  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10371  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10375  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10379  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10383  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10387  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 10391  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 11086  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 11090  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 11094  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 11098  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 11102  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 11106  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 11110  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 11114  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 11118  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 11122  0.0  0.1  43276  3628 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14360  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14364  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14368  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14372  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14376  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14380  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14384  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14388  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14392  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14396  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14408  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14412  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14416  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14420  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14424  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14428  0.0  0.6  43276 14276 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14432  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14436  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14440  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14444  0.0  0.6  43276 14276 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14558  0.0  0.6  43276 14276 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14562  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14566  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14570  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14574  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14578  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14582  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14586  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14590  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14594  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14713  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14717  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14721  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14725  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14729  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14733  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14737  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14741  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14745  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 14749  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15361  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15365  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15369  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15373  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15377  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15381  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15385  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15389  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15393  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15397  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15855  0.0  0.6  43244 14232 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15859  0.0  0.6  43244 14228 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15863  0.0  0.6  43244 14232 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15867  0.0  0.6  43244 14240 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15871  0.0  0.6  43244 14232 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15875  0.0  0.6  43244 14232 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15904  0.0  0.6  43244 14232 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 15994  0.0  0.6  43244 14236 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16048  0.0  0.6  43244 14236 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16052  0.0  0.6  43244 14240 ?        SNs  Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16314  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16318  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16322  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16326  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16330  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16334  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16338  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16342  0.0  0.6  43276 14268 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16346  0.0  0.6  43276 14264 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 16350  0.0  0.6  43276 14272 ?        Ss   Sep30   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0.0 -c socket -d    
tnunamak 31705  0.0  0.6  43276 14268 ?        SNs  10:27   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak 31710  0.0  0.6  43276 14272 ?        SNs  10:27   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak 31714  0.0  0.6  43276 14264 ?        SNs  10:28   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak 31718  0.0  0.6  43276 14268 ?        SNs  10:28   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak 31722  0.0  0.6  43276 14268 ?        SNs  10:28   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak 31726  0.0  0.6  43276 14268 ?        SNs  10:28   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak 31730  0.0  0.6  43276 14264 ?        SNs  10:28   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d      
tnunamak 31734  0.0  0.6  43276 14264 ?        SNs  10:28   0:00 /usr/lib/scim-1.0/scim-panel-gtk --no-stay --display :0 -c socket -d 

```

What's going on?

---

### Post by tnunamak on 2008-10-02
Bump

---

### Post by cosborn72 on 2008-10-05
I noticed that too.  Is it a bug?

---

### Post by iponeverything on 2008-10-05
to see what it is do:

dpkg-query -p scim

---

### Post by aaronb on 2008-10-05
I have only one 'scim' process is would seem.

```
aaron@xyz:~$ ps aux | grep scim
aaron     7613  0.0  0.0   7456   896 pts/0    S+   16:03   0:00 grep scim
```

---

