---
title: "Can't boot off the CD"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by mjrmua on 2005-02-24
I've managed to get my hands on a dogey old laptop (a compaq armada 1580DT according to the stickers on the case) and am trying to install ubuntu.  

But I can't seem to figure out how to enter the BIOS setup program, so despite much wailing and gnashing of teeth, the stupid thing refuses to boot off the CD.

Does anyone know to change bios settings for laptops with "armada 1580DT" stickers on them?

otherwise does anyone have advice on how to install without booting off the CD? 

I can boot of a floppy, but how to create a bootable linux floopy and what to do once it is started?

---

### Post by brainstuff on 2005-02-24
I had a similar problem with a really old Vaio - I ended up restarting the machine about 20 times trying to figure out which key to mash to get it into BIOS - the usual suspects are F1, F2 or Del - pretty sure it was Del that worked for me. Dang sexy splashscreens!

You might also find that one of the keys, or a combo (like shift-escape), will remove the splash screen and reveal the POST underneath.

Good luck
brain

---

### Post by k:arel on 2005-02-24
you can easily make Ubuntu boot floppies with the *dd*  command:

first download the images from:
[ftp://ftp.debian.org/debian/dists/unstable/main/installer-i386/current/images/floppy/](ftp://ftp.debian.org/debian/dists/unstable/main/installer-i386/current/images/floppy/)

(i only downloaded the boot.img and root.img)

then do (while inserting floppies ;)):
```
$ su
# dd if=<dir>/boot.img of=/dev/fd0
# dd if=<dir>/root.img of=/dev/fd0
```

and boot your laptop!

---

### Post by m4ng0 on 2005-02-24
Some links:
[http://www.ubuntulinux.org/wiki/SmartBootManagerHowto](http://www.ubuntulinux.org/wiki/SmartBootManagerHowto)
[http://www.ubuntulinux.org/wiki/Ins...thFloppiesHowto](http://www.ubuntulinux.org/wiki/Ins...thFloppiesHowto)  
[http://www.ubuntulinux.org/wiki/NetbootInstallHowto](http://www.ubuntulinux.org/wiki/NetbootInstallHowto)

Bye,
  Massimo

---

### Post by mjrmua on 2005-02-25
Turns out that the CD dosn't work at all.

Network card is a PCMCIA RTL8139 that isn't detected by etherboot ( has anyone tried etherboot with PCMCIA cards? )

So botting from CD and network don't seem to be possible.

What I do have is a basic debian system from the floppy images that k:arel suggested. 
And access to the files on the Ubuntu CD via a local http server.

Any bright ideas on what to do next?

---

