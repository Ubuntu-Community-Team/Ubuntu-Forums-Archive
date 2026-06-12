---
title: "HOW TO INSTALL: Maple 8"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by Zhukov on 2005-05-30
Ok, i have a copy of Maple 8, but I was unable to install it on my Ubuntu, after a while I've managed to do so...
In case there is someone else woth the same problem, here is the solution:

There is a problem with the jre and the Maple 8 CD.

So, install a JRE (1.4.2 works just fine). You can read how to do this here:

[http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)


Now copy the Maple cd to you hard drive. The desktop for example.
Go to that folder:

cd /home/USERNAME/Desktop/MAPLE_FOLDER/Linux/resources/jre/bin


Now backup the java file:

mv java java.bak


Now lets change the java file:

ln -s /usr/lib/j2re1.4-sun/bin/java java


You can now go back to the Maple main folder and install it:

./installMapleLinuxSU


There is a problem with Maple 8 and the 2.6 Kernels.
This can be easily solved with this:

Create a launcher, in the panel or whathever and link it to this:

export LD_ASSUME_KERNEL=2.4.1 (PATH TO THE XMAPLE FILE)xmaple && (PATH TO THE XMAPLE FILE)./xmaple

If you are in the folder that contains the xmaple file (maple8/bin), you can just run this:

export LD_ASSUME_KERNEL=2.4.1 xmaple && ./xmaple


Enjoy.

---

### Post by Beoras on 2008-01-08
Sadly it does not work for me :(
I just retried the step with the javafile.
First: should the lib actually be existing?
I got Java installed on this machine (sun-java6-bin, sun-java6-jre, j2re1.4), yet the folder you describe is not there (j2re1.4).
Was is there is a folder /usr/lib/j2se/1.4/bin, would that be the file you mean?
This is what I get:
> jujowi@stoepseli:~/tmpmaple/Linux/Linux/resource/jre/bin$ sudo mv java java.bak
jujowi@stoepseli:~/tmpmaple/Linux/Linux/resource/jre/bin$ dir
awt_robot  ControlPanel  i386  java.bak  keytool  policytool  realpath  rmid  rmiregistry  tnameserv
jujowi@stoepseli:~/tmpmaple/Linux/Linux/resource/jre/bin$ sudo ln -s /usr/lib/j2re1.4-sun/bin/java java
jujowi@stoepseli:~/tmpmaple/Linux/Linux/resource/jre/bin$ sudo ../../../../../installMapleLinuxSU
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
rm: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
Suggestions?
Beoras

---

