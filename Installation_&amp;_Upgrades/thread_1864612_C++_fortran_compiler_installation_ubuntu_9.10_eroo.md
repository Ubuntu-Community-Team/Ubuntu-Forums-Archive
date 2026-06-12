---
title: "C++ fortran compiler installation ubuntu 9.10 eroor encountered today..."
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by Surfaero on 2011-10-19
I have installed Ubuntu 9.10 from a CD i recived just 2days before  & got connted to net and it 's workin fine....
for my core work i need to install C /C++ compiler and fortran compiler....
my system is a desktop and has in intel processor it's 32 bit
when i try it from command prompt i have th following error mentioned below...

root@ubuntu:~# sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package g

root@ubuntu:~# sudo apt-get install gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


also when i use synaptic update manager it shows following message
:

root@ubuntu:~# sudo apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update


from menu it has following error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to 192.168.65.171:8080 (192.168.65.171). - connect (111: Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not connect to 192.168.65.171:8080 (192.168.65.171). - connect (111: Connection refused)


kinldy help me out in the installtion of this and fixin it out friends

---

### Post by wayeast on 2011-10-19
I can't pretend to answer your question, since I'm unfamiliar with the ins and outs of the repositories, but here is my thought:

Is there any reason why you can't or don't want to use a more recent version of Ubuntu (downloadable from ubuntu.com)?  Version 9.10 is no longer supported by Canonical.  I don't know if this fact would be important to your issue, but it might help to be using a more recent (supported) version.

---

### Post by Surfaero on 2011-10-20
Firstly thanks for you response...

the second part is how to upgrade 9.10 to 10.4?

---

