---
title: "Ubuntu CD will not install"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by wbmcleod on 2006-09-03
I have a CD with Ubuntu 6.06 for windows machines.  My HP Pavilion Pentium III machine just plain refuses to recognize or intall from the CD.  I have moved starting from disk to the top of the list in the machine setup system (F1 key on restart), and have restarted the system numerous times, but the machine reads the disk (green read light flashes, a lot!) and then simply ignores it and moves on to restart Windows XP Pro as always. Basically the same thing happens if I insert the disk while Windows is running.  The computer reads the disc (the little disk symbol stays on the screen for a while), and then ignores it!
Any suggestions on how to force the computer to accept a new operating system without losing all my data?

---

### Post by meng on 2006-09-03
The obvious possibilities are:
bad download
bad burn
bad CD drive

One test is to try booting from that CD, but on another computer. That would tell you if your drive is the culprit. Your BIOS is probably ok though.

You can check the integrity of the download by checking md5sum.
[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html) in case you don't know how.
If you need to reburn, do it at a low speed.

Your Windows data will be preserved if you install as a dual boot and tell the installer to use available space (in other words, not to use the entire drive).

---

### Post by Geek Dog on 2006-09-03
This may be obvious...but, did you burn the iso to the disc as a disc as opposed to burning the iso file to the disc?

Geek Dog

---

### Post by meng on 2006-09-03
Oh yeah good suggestion, again refer to the link I posted for the proper way to burn the disc image.

---

### Post by wbmcleod on 2006-09-03
Actually, I bought a pre-loaded DVD disc from Amazon, since my computer would also not burn a disc.

---

### Post by meng on 2006-09-03
Okay, then, when you are running Windows and you insert the disc, can you browse the files on it? You can't run the disc while Windows is running (or at least you can't unless you have a virtual machine going), but this will tell you if your CD-ROM drive is working.

---

