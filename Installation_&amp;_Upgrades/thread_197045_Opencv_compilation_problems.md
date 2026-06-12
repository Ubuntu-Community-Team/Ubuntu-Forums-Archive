---
title: "Opencv compilation problems"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by qxrbuklp on 2006-06-15
hello,
     I am new to this forum. I recently installed opencv in ubuntu, I didnt face any problem in installation.  When I tried to compile the sample programs given in opencv, i got them compiled without any difficulties.
   But when I executed a file (say, edge or drawing) I got the following error,

"error while loading shared libraries: libcxcore.so.0: cannot open shared object file: No such file or directory"

 Please help me to solve this problem. I'll be glad if i can get the solution as soon as possible. 

Thanks.

---

### Post by tomchuk on 2006-07-03
I've backported opencv 0.9.7 from Debian Sid to Dapper, I've got source and binary up in my repo, for binaries:
```

deb ftp://robotlab.csis.pace.edu/dapper ./
apt-get install libcv0.9.7-0 libcvaux0.9.7-0 libcvaux-dev libcv-dev libhighgui0.9.7-0 libhighgui-dev opencv-doc python2.4-opencv python-opencv

```

Or from source:
```

deb-src ftp://robotlab.csis.pace.edu/dapper ./
sudo apt-get build-dep opencv
sudo apt-get --build source opencv
sudo dpkg -i *.deb

```

These packages seem to be working quite a bit better that the stock opencv from dapper, or from straight opencv sources - and if they don't work for you, you can just apt-get remove them.

---

### Post by krishreddy on 2006-07-11
I had the same problem and got resolved,
Consider your lib files 'libcxcore.so.0', 'libcv.so.0'...etc. are in the folder /usr/local/lib/ then,
typing the following command will resolve it,

ln -s /usr/local/lib/libcxcore.so.0 /usr/lib/

NOTE: this might give another error of similar kind with different object file, try the same with the object file name changed.

CheErs,

---

### Post by ryanmbruce on 2007-04-22
This is an older thread, but this is still a common problem,so for people that stumbled across the thread:

I talk about this library issue in the following how-to:

[http://www.ryanbruce.org/2006/11/30/installing-opencv-from-cvs-on-ubuntu-edgy/](http://www.ryanbruce.org/2006/11/30/installing-opencv-from-cvs-on-ubuntu-edgy/)

In short, you're getting this error because the executable was built with libraries in (probably) /usr/local/lib/ but the super-nifty program that goes to look for those libraries when you run your program isn't looking in /usr/local/lib.  To get around this, you should add the correct directory to your ld.so.conf file.  (slightly more detailed instructions in the link above)

-Ryan

---

