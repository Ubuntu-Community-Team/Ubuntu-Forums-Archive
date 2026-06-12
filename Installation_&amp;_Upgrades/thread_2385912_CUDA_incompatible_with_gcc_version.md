---
title: "CUDA incompatible with gcc version"
date: 2018-02-26
forum: Installation &amp; Upgrades
---

### Post by papatya2 on 2018-02-26
[INDENT] 					$ apt policy gcc
gcc : Installed : 4:5.3.1-1ubuntu1
        Candidate : 4:5.3.1-1ubuntu1
        Version table :
*** 4:5.3.1-1ubuntu1 500
     500 [http://tr.achive.ubuntu.com/ubuntu](http://tr.achive.ubuntu.com/ubuntu) xenial/main amd64 Packages
     100 /var/lib/dpkg/status

$ inxi -S
  No command 'inxi' found

$ apt-apt-cache policy gcc-5
gcc-5:
    Installed:5.4.0-6ubuntu1~16.04.9    
    Candidate:5.4.0-6ubuntu1~16.04.9
    Version table:
*** 5.4.0-6ubuntu1~16.04.9 500
    500 [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
    500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
    100 /var/lib/dpkg/status
   5.3.1-14ubuntu2 500
    500 [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages

Cuda doesn't support GCC 5.4.0.
[/INDENT]

  $ ./mnistCUDNN

cudnnGetVersion() : 7005 , CUDNN_VERSION from cudnn.h : (7005) (7.0.5)
Cuda failurer version : GCC 5.4.0
Error : unknown error
error_util.h:93
Aborting...

Ubuntu 16.04.9 : Ubuntu 5.4.0-6ubuntu1 : GCC 5.4.0
CUDA Toolkit 9.1
Python3.6.4

[http://docs.nvidia.com/cuda/cuda-ins...n-guide-linux/]("http://docs.nvidia.com/cuda/cuda-installation-guide-linux/")

CUDA Toolkit 9.1 supports gcc5.3.1.

How will I make my gcc version correct ?

---

### Post by QIII on 2018-02-26
You already have at least two threads on this subject.  Please do not start new ones.

Closed.

---

