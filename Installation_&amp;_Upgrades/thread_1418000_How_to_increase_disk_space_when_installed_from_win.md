---
title: "How to increase disk space when installed from windows?"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by mrdmanohar on 2010-02-28
Hi ... I  installed Ubuntu 9.10 from Windows 7 and given 17GB default space for Ubuntu.

I installed different programs and ...now I ran out of disk space when I tried to install Oracle XE.

I tried GParted from Live CD to allocate the space, but it shows the complete partition as single partition for Windows and Ubuntu of which I could not able to allocate the specific space to Ubuntu.

Please help me on this as I don't want to reinstall the Ubuntu again as there's a lot of office work has been done.

---

### Post by cgroza on 2010-02-28
run in terminal 
Code: sudo apt-get clean

This will clear the apt cache so it will release disk space.

---

### Post by mrdmanohar on 2010-02-28
Thanks for the quick reply.

I tried the command ...but still facing the same problem ...


Below is the error I am getting:
******************************************
You have insufficient diskspace in the destination directory (/usr/lib) to 
install Oracle Database 10g Express Edition.  The installation requires at 
least 1.5 GB free on this disk.
dpkg: error processing oracle-xe-universal_10.2.0.1-1.0_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-xe-universal_10.2.0.1-1.0_i386.deb
*********************************************************************

---

