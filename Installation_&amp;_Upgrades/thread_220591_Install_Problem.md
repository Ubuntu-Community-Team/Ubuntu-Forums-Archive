---
title: "Install Problem"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by marvinmatthew on 2006-07-21
Alright, so when I restart my computer with the bootable CD inside, I get this error message:

**"Can't Load DOS! Press Any Key to Continue"**

So I hit return, and the computer restarts itself, and the whole process repeats itself.

Here's my specs:

Intel P4 2.8 GHz
1 Gb PC2700 RAM
(The drive I'm trying to install to is...) 160Gb 5400RPM

Mobo Stuff:
ASUS mobo
Board Form Factor uATX
mPGA478 socket type
800/533/400 MHz FSB
Processor VRM Specification Northwood FMB2

I would certianly appreciate some help in this matter.

-Many thanks.

---

### Post by Kapre on 2006-07-21
Just want to know if your bios is setup to boot from CD? If it is, is your Ubuntu CD a downloaded one or from Ship it? If it is d/lded check its integrity (MD5Sum) and if it is correct and still gives error, burn on a slower speed.

K

---

### Post by marvinmatthew on 2006-07-22
Yes, my BIOS is setup to boot from the DVD-ROM drive that I have the Ubuntu CD in.

It's a version I downloaded from the Ubuntu website.

When I go to burn the CD (I'm using the Ubuntu recomeded CDBurnerXP Pro 3), there are a few options I have to burn the CD with.

First of all, I check "Make Disk Bootable." One I have done this, I get several more options to chose from, they are:
*Emulation Type:*
-Floppy1_20MB
-Floppy1_44MB(95/98/ME Boot Images)
-Floppy2_88MB
-HardDisc
-No emulation (NT/2000/XP Boot Images)

From this list I've been selecting "No Emulation," since I'm using XP.

Then, there are two check boxes, one says "Dissable ISO File Delimeters (;1)." The other checkbox reads, "Enforce ISO Level1 (8 + 3 char max.)"

From these options, I've only been checking the second checkbox (because the buring software checks it by default).

I hope this all makes enough sense. **Would one of you guys be kind enough to tell me what to select/check in among these options?**

*Anyway...*

I'll go ahead and retry while burning at a lower spead, and I tell you the results a little later.

---

### Post by confused57 on 2006-07-22
See this guide for burning an iso:

[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

Is there an option to burn "as an image" in the CD burning program?
Nero has an option make "bootable CD", which is not what is used; but it has an option to burn CD (iso) "as an image"...maybe the program you're using has something similar.

---

### Post by SkyNet2029 on 2006-07-22
You need to uncheck 'make disk bootable', otherwise the burner program drops a small DOS loader on the CD. You want it to load from the Linux on your newly burned image, not DOS. 
All should be well after that.

---

### Post by DetroitBaseball on 2006-07-22
Maybe it would be best to use Alex Feinmann's ISO Recorder, it's a shell. [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

---

