---
title: "Install Hangup?"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by theoflow on 2008-05-26
Just recently started to use Ubuntu/Xubuntu and was looking for some help.  

I have an old laptop laying around (Compaq Presario 1400 series) and can't for the life of me get it to install Xubuntu.  I load the disk and then install but when the status screen pops up it loads up till about 80% and then the screen goes blank.  

If I press the power button again, it will start up, ejects the CD and asks me to remove the disk and restart the laptop.  When I do so and let the computer boot, it says no operating system detected.

System Specs:

600mhz Celeron
512MB of RAM
10 GB Hard Drive
Formated the drive using XP install CD.

---

### Post by dstew on 2008-05-27
Are you sure it really has 512 MB of RAM? Seems like an awful lot for a 600 MHz/10 GB system. The symptom sounds like what happens if there is not enough RAM.

Also, are you sure the disk is OK? Have you used it to install on other computers? Is it a Live CD, or an Alternate Install CD?

---

### Post by theoflow on 2008-06-09
> **dstew said:**
> Are you sure it really has 512 MB of RAM? Seems like an awful lot for a 600 MHz/10 GB system. The symptom sounds like what happens if there is not enough RAM.

Also, are you sure the disk is OK? Have you used it to install on other computers? Is it a Live CD, or an Alternate Install CD?

Checked the specs and it is actually 256 MB of RAM not 512.  Is 256 not enough?

This is the first time I've used this disk so it might be corrupted.  Will burn another to see if it is the disk.

---

### Post by theoflow on 2008-06-15
Ok...it isn't the disk.

I revived an old Compaq desktop with a AMD Duron 750 Mhz with 512MB of RAM and it installed fine.

So just to reiterate the problem, I'm trying to install it on an old laptop and everything boots fine except that when the first load screen for xubuntu shows it, the system goes into hibernate mode about 80% way through that progress bar.  It will not enter the install splash page at all.  When I press the power button again, the load screen displays again telling me to remove the CD and restart.

Any help would be appreciated!  

Thanx in advance

---

### Post by Pumalite on 2008-06-15
How much memory do you have in the machine you are trying to install in?
And what kind of iso are you using to install?

---

### Post by theoflow on 2008-06-15
As stated above, 256 MB

The desktop ISO, not alternative install

---

### Post by Pumalite on 2008-06-15
You cannot boot a Live CD with 256 MB of RAM, unless you make a 500 MB /swap partition ahead of time. I recommend you stick to Xubuntu Alternate CD

---

