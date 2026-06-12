---
title: "Syntax error"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by mahdi109 on 2011-07-05
**when i compile g77 , i have error as below:**


mahdi@ubuntu:~/Desktop/fhi98PP/src$ make
cd ../lib; make -f make.libFREE
make[1]: Entering directory `/home/mahdi/Desktop/fhi98PP/lib'
g77 -c -O  -c -o src.libFREE/dasum.o src.libFREE/dasum.f
/usr/local/bin/g77: 1: Syntax error: word unexpected (expecting ")")
make[1]: *** [src.libFREE/dasum.o] Error 2
make[1]: Leaving directory `/home/mahdi/Desktop/fhi98PP/lib'
make: *** [../lib/libFREE.a] Error 2
mahdi@ubuntu:~/Desktop/fhi98PP/src$ 


[B]please help me.
what is the problem ?[/B]

---

### Post by nzjethro on 2011-07-05
I imagine, for some reason, that there is a syntax error in your g77 file. Run

```
gedit /usr/local/bin/g77
```

and copy-paste the output here. It maybe that it is attempting to access a file whose name has a literal "(" in it, and thus the brackets for the file are mismatched, or something along those lines. If you paste your g77 file here, preferable within [CODE] tags (by clicking the # at the top of the reply window), we'll be able to see what the issue is.

---

### Post by mahdi109 on 2011-07-06
i have this erorr:

Could not open the file /usr/local/bin/g77.

---

### Post by mahdi109 on 2011-07-06
i have this erorr:

Could not open the file /usr/local/bin/g77.

---

