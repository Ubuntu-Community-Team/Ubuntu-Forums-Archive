---
title: "Ubuntu installation problem [Resolved]"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by Lukich on 2006-11-09
I tried to instal Ubuntu 6.06 today and run into the following problem.  I burned the CD and in the Windows Explorer everythig looks great, I can see all the folders for Ubuntu installation and open them up. However, when I reboot it, it simply skips the CD even though set my CD as the first boot device.  So I got the
sbm.bin and use rawrite to put it on a floppy, and when I reboot it, I get the old-school looking start up menue.  In it I try to choose CD-Rom, but get an error saying something like "Error 0X00".  I assume the CD is bad, so I'll try and burn another copy, but my questions is, is there a way to test an installation CD to make sure that it's working properly?  I know I can get this option once Ubuntu starts installing, but I can't get to that stage.
Thank you,
Luka

---

### Post by ner0tic on 2006-11-09
are you burning it as an iso or extracting the iso first then burning the dirs?

---

### Post by aysiu on 2006-11-09
There is a way to check it.

The second part of this tutorial outlines how to do it:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Part 1: Download ISO
**Part 2: Check integrity**
Part 3: Burn ISO

---

### Post by Lukich on 2006-11-10
I extracted it first and then burnt it.  It was the first one in the list:
[http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/)
I guess I should've burnt it as an ISO, yes?

---

### Post by confused57 on 2006-11-10
If the error is coming from the sbm boot floppy...just press "Enter" three times & your CD drive will boot, after you burn the iso correctly per aysiu's tutorial.  You may not even need sbm then, in order to boot the install cd.

---

### Post by Lukich on 2006-11-10
That worked great!  I'm writing this from an Ubuntu desktop.  Thank you guys!

---

