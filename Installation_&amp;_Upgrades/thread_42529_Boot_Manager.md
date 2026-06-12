---
title: "Boot Manager"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by ichiban on 2005-06-18
I have Ubuntu as my regular OS, but I also need several other OS’s installed. I have tried OSL2000 but it could not boot Ubuntu. 

Have anyone gotten OSL2000 to boot Ubuntu, or can I run everything with grub ?

Thanks :smile:

---

### Post by Xian on 2005-06-18
Grub has worked fine for every Linux distro I've tried, plus BSD and windows. 
I'd say stick with it unless you have reason to do otherwise.

---

### Post by ichiban on 2005-06-18
But can grub boot several windows installations? Even on the second harddrive ?

---

### Post by Xian on 2005-06-18
As long as they are properly notated in /boot/grub/menu.lst it shouldn't be a problem.
You could google for some examples.

---

### Post by ichiban on 2005-06-18
Okay I think I got it  :) 

I can use something like this:

title  Ubuntu, 2.6.10 #A 32-bit Ubuntu entry
#This (or something like it) should be in your configuration
root   (hd0,2)
initrd /initrd.img-2.6.10-5-386
kernel /vmlinuz-2.6.10-5-386 root=/dev/hda4


title windows 1
    root (hd0,0)
    makeactive
    chainloader +1

title windows 2
    root (hd1,0)
    makeactive
    chainloader +1

title floppy
    root (fd0)
    chainloader +1

And than check out: [https://wiki.ubuntu.com//RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com//RecoveringUbuntuAfterInstallingWindows)

Thanks  :smile:

---

