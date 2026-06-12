---
title: "Problem regarding installation of libsvm 3.0 in ubuntu 8.10"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by Suvradip on 2011-03-26
I am using libsvm-3.0 for my work.
 When I am trying to install it in my system ubuntu 8.10 i386,it is not getting installed.
 
I had loogged in the system as Super User,then just changing the directory went to libsvm3.0 and tried the "make" command folowing the "READ ME" file.
 It is showing like this -

libsvm-3.0# make
g++ -Wall -Wconversion -O3 -fPIC -c svm.cpp
svm.cpp: In function ‘svm_model* svm_load_model(const char*)’:
svm.cpp:2706: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2710: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2732: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2753: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2755: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2757: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2759: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2761: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2767: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2774: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2781: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2788: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm.cpp:2795: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
g++ -Wall -Wconversion -O3 -fPIC svm-train.c svm.o -o svm-train -lm
g++ -Wall -Wconversion -O3 -fPIC svm-predict.c svm.o -o svm-predict -lm
g++ -Wall -Wconversion -O3 -fPIC svm-scale.c -o svm-scale
svm-scale.c: In function ‘int main(int, char**)’:
svm-scale.c:212: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm-scale.c:213: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
svm-scale.c:220: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result

If I use "make" command next time,it shows 

make: Nothing to be done for `all'.

One thing I would also say that here in libsvm,there is no cfg,so that I can't do ./configure
make 
make check
make install some sort of like this .

I have attached the .tar file of libsvm with this thread.

I need help regarding this problem
Thanks in advance.

---

### Post by Suvradip on 2011-03-26
Te contents of the make file are

CXX ?= g++
CFLAGS = -Wall -Wconversion -O3 -fPIC
SHVER = 2

all: svm-train svm-predict svm-scale

lib: svm.o
    $(CXX) -shared -dynamiclib svm.o -o libsvm.so.$(SHVER)

svm-predict: svm-predict.c svm.o
    $(CXX) $(CFLAGS) svm-predict.c svm.o -o svm-predict -lm
svm-train: svm-train.c svm.o
    $(CXX) $(CFLAGS) svm-train.c svm.o -o svm-train -lm
svm-scale: svm-scale.c
    $(CXX) $(CFLAGS) svm-scale.c -o svm-scale
svm.o: svm.cpp svm.h
    $(CXX) $(CFLAGS) -c svm.cpp
clean:
    rm -f *~ svm.o svm-train svm-predict svm-scale libsvm.so.$(SHVER)

---

### Post by mörgæs on 2011-03-26
8.10 is obsolete. Best is to begin with a fresh install of 10.04 or 10.10.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)
[http://www.releases.ubuntu.com](http://www.releases.ubuntu.com)

---

### Post by Suvradip on 2011-03-29
But Installation of latest version can solve this problem?
Does the version is only constraint in this problem?

---

### Post by mörgæs on 2011-03-29
I can not say for sure that it will solve the problem, but in general people should not be using 8.10. It is a major security threat. 

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by Suvradip on 2011-03-29
Ok.
So according to you it may solve the problem.
But, why did u call 8.10 as "threat" ?

---

### Post by Suvradip on 2011-03-29
Ok I am trying to configure my system  by Ubuntu 10.04.

---

### Post by Dutch70 on 2011-03-29
8.10 is a security threat because it hasn't been supported or gotten security updates for about 1 year. It's outdated.
Whether you will have the same issue with 10.04 or 10.10, is anyone's guess.

---

### Post by Suvradip on 2011-03-29
So, the problem regarding security threats have any impact on the make file or libsvm 3.0  package itself ?

---

