---
title: "SweetHome 3D crash"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by elnetotaca on 2011-01-11
Hello, my name is Neto and I have installed SweetHome 3D and for some reason, the window will close as soon as I try to click on any item on that particular window.
here is what I have;

x@Hell:~$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.2) (6b20-1.9.2-0ubuntu2)
OpenJDK Server VM (build 19.0-b09, mixed mode)
x@Hell:~$ 


and here is what the problem is;

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb76f0424, pid=22090, tid=1738611568
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Server VM (19.0-b09 mixed mode linux-x86 )
# Derivative: IcedTea6 1.9.2
# Distribution: Ubuntu 10.10, package 6b20-1.9.2-0ubuntu2
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#

any ideas??
I will much appreciate some help, I can't find the cure.
Neto.


I downloaded the latest version from their website, it comes with java already.

---

### Post by Jack Brown on 2011-02-27
Hi neto,

you can try **sun-java6-jre** instead of openjdk.  you might need to enable 'canonical partners' in your Ubuntu Software Center -> Software Sources to be able to see this.  

Just type in JRE in software center and it should appear.

Not sure if you have to uninstall openjdk first though.

Another thing you can try is to download sweethome3d with java bundled. from [http://www.sweethome3d.com/download.jsp](http://www.sweethome3d.com/download.jsp)

have a nice day!

---

### Post by elnetotaca on 2011-07-06
worked fine, im back from the hospita, and thats why i was away from the pc.
Thanks

---

