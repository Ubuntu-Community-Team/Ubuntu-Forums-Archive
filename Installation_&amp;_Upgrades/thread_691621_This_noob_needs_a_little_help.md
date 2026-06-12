---
title: "This noob needs a little help"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by SIXAXIS on 2008-02-08
I have downloaded Super Mario War's binary code for Linux. It is named SMW.tar.gz. I know how to extract this with the console, but how do I compile and install/run it?

---

### Post by taurus on 2008-02-08
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

Or the whole thing, [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/).

---

### Post by SIXAXIS on 2008-02-09
I don't know which folder to go into. I tried it from the folder which has both usr and install folders. I also tried it from within the folders. I get the error:

make: *** No rule to make target `install'.  Stop.

I also tried to /.configure and it says that there's no file or folder called that.

What should I do?

---

### Post by SIXAXIS on 2008-02-09
I re-extracted it and now when I try to install, it gives me the error:

make: Nothing to be done for `install'.

Maybe it's because there's only a text file in the install folder?

---

### Post by taurus on 2008-02-09
If it is a binary code, then you just run it where you unpack it, usually.  However, sometimes, there would be a install script, install.sh or something similar to that, that you can run to install it it on your machine.  

Make sure you are in the directory where you have unpacked it, then post the output of this command here.

```
ls -la
```
Otherwise, where did you download it so I can have a look at it and see what do you need to do then?

---

### Post by SIXAXIS on 2008-02-09
Here is the la -la output:

andrew@andrew-laptop:~/Firefox Downloads/Super Mario War/smw$ ls -la
total 16
drwxr-xr-x 4 andrew andrew 4096 2008-02-09 09:41 .
drwxr-xr-x 3 andrew andrew 4096 2008-02-09 09:54 ..
drwxr-xr-x 2 andrew andrew 4096 2007-03-28 07:18 install
drwxr-xr-x 5 andrew andrew 4096 2007-03-28 07:18 usr

---

### Post by SIXAXIS on 2008-02-09
Also, when I did a checkinstall, it came up with this:

andrew@andrew-laptop:~/Firefox Downloads/Super Mario War/smw1.7$ checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> Super Mario War 
>> 

*****************************************
**** Debian package creation selected ***
*****************************************
/usr/bin/checkinstall: line 1166: dpkg-architecture: command not found

This package will be built according to these values: 

0 -  Maintainer: [ andrew@andrew-laptop ]
1 -  Summary: [ Super Mario War ]
2 -  Name:    [ smw1.7 ]
3 -  Version: [ 20080209 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ smw1.7 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Makefile:13: configuration: No such file or directory
make: *** No rule to make target `configuration'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up.../usr/bin/checkinstall: line 302: [: too many arguments
OK

Bye.

---

### Post by taurus on 2008-02-09
Do you see the **install** directory from your previous post?  Look in there.

```
cd install
ls -la
```

---

### Post by SIXAXIS on 2008-02-09
ls -la in the install folder:

andrew@andrew-laptop:~/Firefox Downloads/Super Mario War/smw/install$ ls -la
total 12
drwxr-xr-x 2 andrew andrew 4096 2007-03-28 07:18 .
drwxr-xr-x 4 andrew andrew 4096 2008-02-09 09:41 ..
-rw-r--r-- 1 andrew andrew  295 2007-03-28 07:18 slack-desc

---

### Post by taurus on 2008-02-09
Wait a second.  It looks like you have downloaded the package for Slackware system where it has .tgz extension.  So, you have to install it in _Slackware_ with 

```
installpkg filename.tgz
```
Again, I will try to ask this one more time.  Where did you download it from?

---

### Post by SIXAXIS on 2008-02-09
> **taurus said:**
> Wait a second.  It looks like you have downloaded the package for Slackware system where it has .tgz extension.  So, you have to install it in _Slackware_ with 

```
installpkg filename.tgz
```
Again, I will try to ask this one more time.  Where did you download it from?
I downloaded it from the official website. All they have for Linux is the source. Anyways, I'll try the Slackware thing. Thanks for your help, I appreciate that you took the time to help me with my problem.

---

