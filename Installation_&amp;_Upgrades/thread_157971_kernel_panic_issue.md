---
title: "kernel panic issue"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by Dragon56 on 2006-04-10
I am trying to run ubuntu 5.10 - installed.
It is a multiboot with fedora, mandriva, mepis, ark, vector and xandros.
All run OK from the fedora grub except vector which requires a boot floppy.
I use fedora as my main distro, but am not really happy with it.

I have installed ubuntu and set grub/menu1st to ¨see¨ ubuntu correctly.
file reads:
title ubuntu
	rootnoverify (hd0,12)
	kernel /boot/vmlinuz-2.6.12-9-386 root=dev/hda12 
	initrd /boot/initrd.img-2.6.12-9-386

ubuntu appears to be booting, then I receive the following:
Begin: Initializing /dev.../init:76:divide by zero
[4294679.548000] kernel panic - not syncing: attempting to kill init!
[4294679.548000

I am not a seasoned linux user, but can use common sense. It has served me well until now. I would appreciate some ideas on what I need to correct this problem. Thank you.

---

### Post by Kapre on 2006-04-10
dragon56 - on your Grub menu, are all other distros working perfectly? Kernel Panic is a message saying that there is something wrong or missing on your kernel (maybe a bad install). Try reinstalling again and make sure that your source (CD) is in perfect working condition.

K

---

### Post by Dragon56 on 2006-04-10
Yes, all others work. Fedora works with w/ kernel info (don´t know proper description of command, sorry) like ubuntu;  most others work from chainloader 1+ command. Vector is exception, runs from boot floppy.
I will try re-install: is the a particular kernel choice, of the three, that would be better for this install?
The CD was a straight mail from ubuntu.

---

