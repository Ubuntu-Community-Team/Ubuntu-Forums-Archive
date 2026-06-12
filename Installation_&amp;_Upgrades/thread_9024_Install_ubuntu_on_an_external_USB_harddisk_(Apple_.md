---
title: "Install ubuntu on an external USB harddisk (Apple PowerBook)"
date: 2004-12-23
forum: Installation &amp; Upgrades
---

### Post by itymoneus on 2004-12-23
I am trying to install the PowerPC-Edition of Ubunto 4.1 onto an external USB2 harddisk on an Apple PowerBook G4 12" while preserving my MacOS on my internal harddisk.
Everything (network setup, automatic partitioning, installation of packages) went fine till the installation of yaboot, it  begins, takes a long time, and stops then in the process of identifying other operating systems. It simply fails with an error text like "not possible to install the boot loader. Continue without yaboot ?".
Experiments with manual partitioning, expert/custom installation mode, etc. went equally wrong. Experiments with installing the bootstrap-partition onto my internal harddisk are on hold, because i first need to know some details (see below).

Some detailed questions:
 a) Is it possible to install Ubunto onto an external USB2 harddisk without touching the MacOS installation ? Or do i need to install it partially onto my internal disk ?
 b) I did not get the linux binary ofpath up and running, therefore i do not now which boot-string open-firmware (OF) needs for direct booting my installed (but yaboot-less) linux. The installer said linux has been installed to /dev/sda3 (and i can mount it that way), is there a way to install it directly ?
 c) Is there any good information material about installing Ubuntu onto Macs resp. external harddisks of Macs ?
 d) Is it possible to start a linux on my external harddisk without yaboot only by using the installation CD ? (Currently i do not want to disturb my MacOS and for the first steps this *workaround* may be applicable).

I appreciate your help. Thanks !

Farvel
 Itymoneus

---

### Post by itymoneus on 2004-12-27
I now tried to install ubuntu on the external usb harddisk while installing yaboot and /boot onto the internal disk. The installation went fine, the boot-process looks fine, but if i select Linux at the yaboot boot prompt i get errors.

 ...
 PCI: Cannot allocate ressource region 0 of device ....
 PCI: Cannot allocate ressource region 0 of device ....

 audit (...): initialized
 Starting ubuntu....
 pivot_root: No such file or directory
 /sbin/init: 429: cannot open dev/console: No such file
 Kernel panic: Attempt to kill init!

It seems that the system is able to get the linux kernel up and running, but the ubuntu installation (on the external disk) is not available to him, so it fails. The lamp of my usb disk is pitch black, so i assume, that neither the OpenFirmware nor the kernel started the usb disk. 

Any ideas ?
 Itymoneus

---

### Post by javamdk on 2005-02-23
YaBoot can't boot from external devices yet... such as firewire or usb  ](*,)

---

### Post by itymoneus on 2005-03-12
'yet ' ? Are there any plans supporting that ? Is there any code to test with ?

---

### Post by javamdk on 2005-03-12
Just read recently this article:
[http://www.sharplabs.com:8668/space/Using+an+external+disk+gizmo+-+New+World](http://www.sharplabs.com:8668/space/Using+an+external+disk+gizmo+-+New+World)

Same thing, only in a better how-to format is:
[http://131.204.27.45/ydl-howto/](http://131.204.27.45/ydl-howto/)

It's all using Yellow Dog linux, but might work with ubuntu.  

Yet some more usefull information:
[http://lists.terrasoftsolutions.com/pipermail/yellowdog-general/2003-October/010501.html](http://lists.terrasoftsolutions.com/pipermail/yellowdog-general/2003-October/010501.html)

This is new to me... so it's kind of in depth stuff -- if you're up for a project, go for it!

---

