---
title: "UbuntuStudio - installing wireless card RT61"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by ShaQti on 2008-10-05
Hi, I'm a beginner to linux. I have installed a UbuntuStudio on my system. I want to configure my wireless card ( RaLink RT2561 / RT61 ) for the internet. I have downloaded the driver from the Ralink website through another windows machine and copied the files to Ubuntu machine's home directory. The ReadMe file inside the package, has the Build Instructions as follows:

1. $cp Makefile.6 ./Makefile ( was done successfully )

2. $make all ( error )

It gives the following error :
make -C /lib/modules/2.6.24-19-rt/build SUBDIRS=/home/shaqti/2008_0723_RT61_Linux_STA_v1.1.12.2./Module modules 
make: ***/lib/modules/2.6.24-19-rt/build: No such file or directory. Stop.
make: *** [all] Error 2

When I go to the directory /lib/modules/2.6.24-19-rt/ , there is no directory called build.
There is also another directory /lib/modules/2.6.24-19-generic, where there is a sub-directory by name 'build'.

Please help me out.

I would like to instally my wireless cards. Thanks

---

### Post by lemming465 on 2008-10-11
You could try doing ```
sudo ln -s 2.6.24-19-generic /lib/modules/2.6.24-19-rt
```, but I suspect you will run into other errors after that.

An alternative possibility is to install a windows driver using *ndiswrapper*.

---

### Post by tommcd on 2008-10-12
The driver for Ralink rt61 is part of the kernel now. My rt61 card worked out of the box in Ubuntu 8.04. I have not used Ubuntu Studio, but I would think it should work out of the box on Ubuntu Studio also. Run **sudo lsmod**. See if rt61pci, rt2x00pci, rt2x00lib are running. If not, just **sudo modprobe rt61pc1**. Then set up your wireless with ifconfig and iwconfig, or use system > administration > network to set it up. Write back if you need more help.

---

### Post by kvk on 2008-10-12
I'm running an RT61 as well- try downloading the newest daily cvs file. I'm able to get things up and running, but the connection itself doesn't fetch any pages, even though it's active. The solution is still being explored. 

I'm going to be loading Ubuntu Studio too, so we'll see how it all fits together. :)

[http://ubuntuforums.org/showthread.php?t=939422](http://ubuntuforums.org/showthread.php?t=939422)

---

### Post by Kyle54 on 2008-10-12
Same exact problem here. the (generic) folder has a folder called build, and i think it'd work if it would copy there.

but it wants me to copy to the other one. the non-generic one.
so wireless is a no go.

---

