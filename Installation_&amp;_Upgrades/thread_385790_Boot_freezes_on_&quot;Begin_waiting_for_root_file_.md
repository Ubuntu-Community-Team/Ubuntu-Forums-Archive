---
title: "Boot freezes on &quot;Begin: waiting for root file system&quot;"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by kevpatts on 2007-03-16
Hey all,

I was using Ubuntu yesterday and all was fine. I connected my Sony Ericsson k800i and viewed some photos and stuff, installed the updates of the day (I have Universe and Multiverse enabled) and then shut down. I added an extra hard drive and then tried to boot up again and my boot hangs at the above message every time! Even in single user mode. If I have USB devices it goes a little further, and says something like "usb4-1: configuration #1 chosen from 1 choice" but I don't think that's related because whther I have USB devices connected or not it still won't boot. I've removed the new hard drive too and still no luck. Any clues?

I'm dual-booting with Vista and everything's been working fine till now, but Ubuntu is my default and so I need it back! Can the Live CD help me?

Kevpatts

---

### Post by kevpatts on 2007-03-22
I'm still having problems with this. I'm trying to mount my root filesystem from a LiveCD boot but am having trouble locating useful logs on it. Where could I find a relevant logfile?

---

### Post by kevpatts on 2007-03-28
Found the fault.

I'd accidentally changed my Main bootable hard drive from Secondary Slave to secondary Master. To fix the system I had to alter /boot/grub/device.map so that (hd0,0) was /dev/hdc instead of /dev/hdd and I had to replace all instances of /dev/hdd2 with /dev/hdc2 in /boot/grub/menu.lst also.

---

### Post by andguent on 2008-05-29
I know it has been a year, but thanks for following up to your own post with the answer. The error message is still the same in hardy. 

You reminded me that I changed drive letters around recently, but got distracted at the phase where I should have updated my grub files.

---

### Post by kevpatts on 2008-05-30
No problem. Glad it was helpful to someone.

Kevpatts

---

