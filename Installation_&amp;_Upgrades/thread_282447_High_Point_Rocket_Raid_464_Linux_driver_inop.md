---
title: "High Point Rocket Raid 464 Linux driver inop"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by Dreadknott on 2006-10-22
Hi all, and thanks for being here for me...

I am building a server using Highpoint Rocket Raid 464 PCI card and eight IDE HDD's.

The tutorial is explained at [http://www.finnie.org/text/terabyte/](http://www.finnie.org/text/terabyte/)

The soft raid card's drivers are at [http://wwww.highpoint-tech.com/USA/bios_rr464.htm](http://wwww.highpoint-tech.com/USA/bios_rr464.htm)

They have iso's for install disks for Redhat, Fedora, Suse, and Source for everyone else.

I have folowed directions to the best of my ability for Source install and dissabled auto detection of my raid drives by adding hde=noprobe through hdl=noprobe in /boot/grub/menu.lst

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single hde=noprobe hdf=noprobe hdg=noprobe hdh=noprobe hdi=noprobe hdj=noprobe hdk=noprobe hdl=noprobe
initrd		/boot/initrd.img-2.6.15-27-386
boot

This is as far as I can get because when I run the make file as outlined in the readme.txt all I get are errors installing.
 sudo make KERNELDIR=/usr/src/linux-2.6.15-27

Here are some of the errors...

entry.c:499: error: dereferencing pointer to incomplete type
entry.c:499: error: dereferencing pointer to incomplete type
entry.c:500: error: dereferencing pointer to incomplete type

In file included from hpt.c:171:
vdevice.c: In function ‘__fRegisterVDevices’:
vdevice.c:71: warning: incompatible implicit declaration of built-in function ‘m emset’
vdevice.c: In function ‘fCheckBootable’:
vdevice.c:188: warning: incompatible implicit declaration of built-in function ‘ memset’
vdevice.c: In function ‘AllocateCommand’:
vdevice.c:291: warning: incompatible implicit declaration of built-in function ‘ memset’
In file included from hpt.c:172:
init.c: In function ‘InitializeAllChips’:
init.c:18: warning: incompatible implicit declaration of built-in function ‘mems et’
init.c: In function ‘fGetChannelTable’:
init.c:129: warning: incompatible implicit declaration of built-in function ‘mem set’
init.c: In function ‘fGetDeviceTable’:
init.c:140: warning: incompatible implicit declaration of built-in function ‘mem set’
make: *** [hpt.o] Error 1

Could someone Dl the Source from the link above, check the makefile and readme to see whats going on?

I'm pretty lost with all these errors and I bought the card because it had Linux drivers available on the website...

Thanks!

---

### Post by Dreadknott on 2006-11-03
Update...

RR464 drivers work for old redhat, and Fedora 1,2,3,4, but not five, or Suse 10.

Can not upgrade FC4 and Highpont doesnt care about compiling for Debian.

I'm going to dump the card and try another.

---

