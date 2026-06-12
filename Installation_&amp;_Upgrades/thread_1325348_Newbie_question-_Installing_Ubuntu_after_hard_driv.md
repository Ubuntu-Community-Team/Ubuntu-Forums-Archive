---
title: "Newbie question- Installing Ubuntu after hard drive wipe"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Torri on 2009-11-13
Hi everyone, brand new here.
 
I have an XP laptop that is horribly infected, and I want to completely wipe it (not just reformat) and install Ubuntu over the charred ashes of XP. There's nothing on it that I need. I want to use Killdisk, but I've never used it before and I'm afraid I won't be able to boot Ubuntu from the disk after using it.
 
Does anyone know how to do this, or have suggestions?? Thanks!

---

### Post by snowpine on 2009-11-13
Hi Torri,

The Ubuntu installer has a "Guided: Use entire disk" option. This would be the easiest solution.

---

### Post by kestrel1 on 2009-11-13
Have a look at my web site & look under tutorials for installing Ubuntu. Email me if you have any questions:
[http://www.kcsdorset.co.uk](http://www.kcsdorset.co.uk)

---

### Post by Torri on 2009-11-13
Thanks for the responses!
 
> **snowpine said:**
> 
 
The Ubuntu installer has a "Guided: Use entire disk" option. This would be the easiest solution.
 
Right, I understand you can do that. Let's say I'm selling the computer (I'm not, but for example), so I need to completely wipe it and start fresh with Ubuntu. By wipe, I mean overwrite and so destroy all data.

---

### Post by snowpine on 2009-11-13
Ubuntu can be installed on a blank hard drive (if I understand your question correctly).

---

### Post by kestrel1 on 2009-11-13
> **Torri said:**
> Thanks for the responses!
 

 
Right, I understand you can do that. Let's say I'm selling the computer (I'm not, but for example), so I need to completely wipe it and start fresh with Ubuntu. By wipe, I mean overwrite and so destroy all data.
If you want to be sure that all data is erased from the drive you need something like Drive Cleanser
[http://www.acronis.com/enterprise/products/drivecleanser/index.html](http://www.acronis.com/enterprise/products/drivecleanser/index.html)
There may be some open source programs that will do the same job though.

---

### Post by darkod on 2009-11-13
This has free version. I think the free allows only one pass but you can run it several times.
[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

---

### Post by audiomick on 2009-11-13
I think I remember reading that a Gparted live CD includes an overwrite function, i.e. all data really gone,not just address tables
[http://en.wikipedia.org/wiki/Gparted](http://en.wikipedia.org/wiki/Gparted)
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
Burn the ISO on to a CD, boot from it, run the function.
If I'm wrong, and gparted can't do it, it can at least remove all the partitions from the disc.
A bit of searching should turn up a utility that can do a complete wipe. I look for that a few months ago, out of curiosity, and found several within 20 minutes.

As Far as the Ubuntu install goes, though: If you run the installer and go into the manual partitioning option, you get to see what it is doing. Even if you just go ahead and accept it's suggestion, you can see that it has identified the whole disc. You also have the ability here to set up partitions as you need them. A good plan is to make a separate partition for / and for /home. The swap partition should be a bit bigger than your RAM.

This might be worth a read:
[http://ubuntuforums.org/showthread.php?t=1321649](http://ubuntuforums.org/showthread.php?t=1321649)

Edit:I see darkod has suggested Killdisk. I think your fear of not being able to start Ubuntu afterwards is unfounded. Having the computer boot from the CD is a function of the BIOS settings. I have started a computer from the Ubuntu live CD the had NO hard disc in it at all.

---

### Post by Torri on 2009-11-13
Yes, I have Killdisk. My question is, what happens after I use it? Will I be able to install Ubuntu without any problems? I'm worried that Killdisk is going to destroy the systems I take for granted, for example getting my laptop to spit out the CD tray and being able to read the install disk.

---

### Post by darkod on 2009-11-13
It just "kills" the data. Of course it will not destroy your computer. :)
I have used it on a hdd I was selling. The buyer didn't come back to complain. :)

Although, since you plan to install ubuntu on your hdd I see no reason to wipe data at all.

---

### Post by BrandonBan6 on 2009-11-13
I've never used killbox for a disk wipe out utility, check out [Darik's boot and nuke,]("http://www.dban.org/") it'll delete/overwrite the data to DOD standards. 

From there, you can install Ubuntu with no issues (the installer will format the disk to whatever format you use, I'd pick ext4).

---

### Post by audiomick on 2009-11-13
Hallo again, in case you don't backtrack to my edit. I have started a computer fro the Ubuntu Live CD that had NO hard disc in it at all.

---

### Post by Torri on 2009-11-13
Allright, well I think since most people seem to think it's a non-issue, I'll just try and install without the complete obliteration. I can always go back and do it again, if I have problems.
 
Thanks everyone, for all your input! I'm sure I'll be back.

---

### Post by audiomick on 2009-11-13
good lad, that's the spirit!

---

### Post by Torri on 2009-11-13
Aaaand I come to a screeching halt.
 
Installation freezes at the "welcome, ready to install?" screen. I checked the disk- OK, tested the memory-  OK. It's kind of an oldish laptop (5 years old, gateway running on an intel celeron). I really hoped it would be able to handle this. Any thoughts??

---

### Post by kestrel1 on 2009-11-13
How much RAM have you got in it & what is the speed of the CPU?

---

### Post by Torri on 2009-11-13
I think 256 and I'm not sure about the CPU. It's not super fast or anything though... The Celeron was the base model I think. I don't even use that laptop anymore because of the viruses... It's basically completely unusable. I wanted to switch all our systems to Linux, but first I wanted to try it out on the infected laptop, in the hopes that it could be saved.

---

### Post by audiomick on 2009-11-13
Have you already broken off the install? I might be interesting to boot the machine from the live CD and see how it deals with Ubuntu. If it is having lots of trouble, I believe Xubuntu is less resource intensive.

---

### Post by snowpine on 2009-11-13
256mb is borderline for a modern Linux system (I think 384mb is the minimum to install Ubuntu using the Live CD). You could try the text-based Alternate Install CD, or a lighter-weight distro (Xubuntu is popular). Increasing the RAM is the best option, of course.

---

### Post by kestrel1 on 2009-11-13
Personally I would opt for Xubuntu, puppy Linux or similar.

---

### Post by Torri on 2009-11-13
Hmm okay. I'll try the text-based installer first, and if that doesn't work I'll give Xubuntu a try. 
 
Thanks again! (I'm sure I'll be back.) :)

---

