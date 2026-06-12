---
title: "apt-get unable to locate alien package in Ubunutu-12.04"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by jaynarayan on 2013-03-19
Hi Ubunuters,

    I have to install following rpm packages in my ubunut-12.04 with x86_64 system
 
   kernel-2.6.18-1.2798.fc6.x86_64.rpm  
   kernel-devel-2.6.18-1.2798.fc6.x86_64.rpm  
   kernel-headers-2.6.18-1.2798.fc6.x86_64.rpm

  So I tried to install  "alien" to convert rpms to debs. I tried to install using :sudo apt-get install alien hower I got an error - E: Unable to locate package alien. 

Next I tried to down load alien tar.gz package and manage to install it. Then when I tried to run the following command: 
sudo alien  kernel-2.6.18-1.2798.fc6.x86_64.rpm   it gave me the following error msg.
---------
sh: 1: rpm: not found
Error executing "LANG=C rpm -qp --queryformat %{NAME} 'kernel-2.6.18-1.2798.fc6.x86_64.rpm'":  at /usr/local/share/perl/5.14.2/Alien/Package.pm line 489
------------

then I tried googling and did some experiment to get things done howevre no hope. 

Please suggest me a diamond like solution.

Thanks  and cheers 
JaYnArAyAn
------

---

### Post by arpanaut on 2013-03-19
You do know that 12.04 is using kernel 3.2.0-38 currently.
If you need to use an older kernel you should look for .deb packages which are native to debian/ubuntu.
If you do install that old of a kernel in 12.04 you are going to run into all kinds of dependency issues,
and conflicts with packages and abi's etc. It may be possible to do this but I doubt if it would be easy.

I don't know what you are trying to accomplish or why but you may need to rethink what you are doing

---

