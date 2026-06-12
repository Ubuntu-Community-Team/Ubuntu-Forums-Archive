---
title: "Fan running constantly in Dell Inspiron 3521 after upgrade to 14.04"
date: 2014-10-22
forum: Installation &amp; Upgrades
---

### Post by davy jones on 2014-10-22
I'm summing up my entire problem from the beginning so that it would be easier for someone to help after getting some history on the system.

My Inspiron 3521 came with Windows 8 pre-installed. It has 4 GB RAM, hybrid Intel/AMD graphics (Radeon HD 8700), BIOS version A05 and UEFI. I bought it last year and I installed 12.04.2 alongside Windows, but in Legacy. The system worked fine for a year. I had even managed to install flgrx and AMD Catalyst Control Centre to enable only the Intel GPU, which had doubled my battery life.

A few weeks ago I inadvertently installed some hardware support update which disabled or corrupted the graphics driver or something like that. My system was giving problems and it said that my /boot partition was full. I did some cruft cleanup using Ubuntu Tweak after which Ubuntu would not start. It would just freeze on a black screen after startup. I thought it was a boot problem, so I ran Boot Repair, which basically converted my Legacy install into a UEFI install. This did not solve my problem.

I had no choice but to install 14.04. I did in from a live USB in UEFI mode this time. I deleted the /boot partition using Gparted in the live session, expanded / to fill up that space. I selected the Something Else option for the installation, re-used the / partition after formatting it, and kept the /home partition without formatting, because it had my data and settings.

My first priority obviously was to install the AMD driver because my battery wasn't lasting very long and the fan was constantly running. I managed to install it using Additional Drivers and selected my preferred options in CCC, but the fan is still running constantly. It starts running at the drop of a hat.

Any help would be appreciated, and since I'm not very tech-savvy simplified instructions would be even more appreciated. Thanks in advance.

---

### Post by davy jones on 2014-11-07
I've noticed that this generally happens when I'm on AC power.

---

### Post by anchitsingh9 on 2014-12-23
Check this out:

[http://ubuntuforums.org/showthread.php?t=2240312](http://ubuntuforums.org/showthread.php?t=2240312)

---

