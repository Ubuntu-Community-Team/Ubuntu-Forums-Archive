---
title: "[SOLVED] Running Ubuntu 8.10 from a bootable USB HDD"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by sameera on 2008-11-01
HI,
I've decided to try out Ubunutu once again (I'm a long time Windows user, trying honestly to convert).

So, I booted up from the CD and mistakenly installed GRUB to my internal HD :(
After installation I got the blank screen described [here]("http://ubuntuforums.org/showthread.php?t=966337"). So I rebooted and kept getting GRUB Error 21 (as I remember). So, I restored the Windows MBR (with fixmbr from windows boot cd) and now I can get into my Windows installation. I can also use the Live CD version without a prob.

Now before I do anything, I want to make my USB HDD (that has the Ubuntu installation) bootable. I.e. to install GRUB in to the USB drive's MBR. I think there's something like
GRUB
root (hd1,0)
etc.
But when I run the above command from the live CD, it says hd1 is not there. 
Any help?
Thanks.

---

### Post by caljohnsmith on 2008-11-01
How about trying this from your Live CD:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should be all it takes to install Grub to the MBR of your USB drive. Let me know how it goes, or if you run into problems. :)

---

### Post by sameera on 2008-11-02
Thanks. That did it.

---

### Post by caljohnsmith on 2008-11-02
Glad it worked. Cheers and have fun with Ubuntu. :)

---

