---
title: "Dell Inspiron 1501: Fixing recursive fault but reboot is needed"
date: 2014-01-28
forum: Installation &amp; Upgrades
---

### Post by dan-du on 2014-01-28
So, I installed the AMD64 version of Ubuntu 13.10 and I got through the installer, but when trying to reboot, I got this error.
I tried the usual "acpi=off" and other related commands, but it didn't work. People have reported this problem when trying to boot from different power sources (such as battery or AC), but I only have an AC adapter for this laptop.
I have the latest 2.6.3 BIOS, 120GB WD HDD, 3GB of RAM, 2GHz AMD Sempron (one core), and I installed with the updates (and I tried without.)

---

### Post by dan-du on 2014-01-30
So, I installed the AMD64 version of Ubuntu 13.10 and I got through the installer, but when trying to reboot, I got this error.[COLOR=#000000]I tried the usual "acpi=off" and other related commands, but it didn't work. People have reported this problem when trying to boot from different power sources (such as battery or AC), but I only have an AC adapter for this laptop. [/COLOR][COLOR=#000000]I have the latest 2.6.3 BIOS, 120GB WD HDD, 3GB of RAM, 2GHz AMD Sempron (one core), and I installed with the updates (and I tried without.)[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by dan-du on 2014-01-30
...So, I installed 12.04.3 LTS, and it worked.
But yknow, I install all of the 250 or so updates.
And it doesn't work anymore. I have tried to boot into the older kernel, but it doesn't fix the problem...

---

### Post by mörgæs on 2014-01-31
Please stop multiposting. Merged.

It would be good with knowing the hardware. Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by dan-du on 2014-01-31
Sorry about the multiposting, I thought this section was more appropriate, but turns out you cannot delete your threads...
Here:

---

### Post by mörgæs on 2014-02-01
If you want a thread moved you have to report it, also if it's your own.

The Radeon Xpress 200M should not be that hard to deal with. How does it work if you install the text-only [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

---

### Post by dan-du on 2014-02-01
But it does work, but it fixes recursive fault but reboot is needed when I install the updates

---

### Post by dan-du on 2014-02-02
So, apparently, upgrading to a highly unstable version of 14.04 seems to fix all the problems I had... (even after installing updates) so.. yeah...
Also, do you know a version of fgrlx that works with my GPU?

---

### Post by mörgæs on 2014-02-02
Congratulations and thanks for testing 14.04. Please report bugs if you find any, and please mark the thread 'solved'.

There are no fglrx drivers for this card, only the open-source radeon drivers.

---

### Post by dan-du on 2014-02-03
Is there anything that supports 3D acceleration for running Steam games (like Half-Life 2)?
HL2 works fine on windows, but I get an OpenGL error on linux (haven't tested Wine)

---

### Post by mörgæs on 2014-02-03
I don't know. 
This is a new question, please open a new thread with the lshw output.

---

### Post by dan-du on 2014-02-03
Okay, will do that

---

### Post by hoozy on 2014-03-17
I had the same problem develop with my Dell 1501 after doing an upgrade.  I booted the system into the previous kernel by selecting the options choice in the grub boot menu.  I found that I could boot using kernel 3.08 but not 3.11.  I Googled some and found a site named [www.randarlabs.com](www.randarlabs.com) that had a script that allowed me to install the latest kernel, version 3.13.  I did this by booting using the 3.08 kernel and then downloading and running the kernel upgrade script from the randarlabs site.  Something is funky in the 3.11 kernel that my Ubuntu 13.10 installation did not like.  Everything seems to be normal again now that I've upgraded the kernel to 3.13.  Now I'm wondering if the kernel upgrade is going to mess up the upgrade to the next version of Ubuntu in April.  I hope what I've discovered helps someone with their Dell.  I have gotten so much help from the community that I'm glad to be able to contribute something back.  *smile*
-- Don

---

### Post by hoozy on 2014-03-18
Well, I knew it was too good to last.  When I changed to the newest kernel both the ethernet cable connection and the wifi connection on my 1501 stopped working.  I was still able to use the advanced options in grub to revert back to the 3.08 kernel and boot my system (with wifi working again after bootup).  Since the early release beta of Ubuntu version 14.04 is now available I am upgrading my 1501 to it after I did a full backup using Clonezilla.  I will update here with the results of the upgrade when it finishes doing the upgrade this morning.
-- Don

---

### Post by hoozy on 2014-03-18
The upgrade to the beta version of 14.04 aborted while telling me that the system may have been left in an unstable state.  I guess for now I will recover the system from my Clonezilla backup and change grub to boot the 3.08 kernel by default.  I suspect that the finished 14.04 upgrade will fix the Recursive Fault problem but not until April, of course.  My advice right now is to keep using the 3.08 kernel if it works for you and try the upgrade to 14.04 next month.
-- Don

---

