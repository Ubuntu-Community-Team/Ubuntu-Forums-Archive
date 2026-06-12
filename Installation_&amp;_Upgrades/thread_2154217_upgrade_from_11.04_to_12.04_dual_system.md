---
title: "upgrade from 11.04 to 12.04 dual system"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by Kenc3 on 2013-06-13
I am trying to go from Ubuntu 11.04 to 12.04. Do I have to go through all the different releases or can I just go from one to 12.04?
 I am presently upgrqading from 11.04 to 11.10.
 I have a dual system with Windows7 and it will not let me boot from a USB.
Ken

---

### Post by Bucky Ball on 2013-06-13
> **Kenc3 said:**
> I am trying to go from Ubuntu 11.04 to 12.04. Do I have to go through all the different releases or can I just go from one to 12.04?
 I am presently upgrqading from 11.04 to 11.10.
 I have a dual system with Windows7 and it will not let me boot from a USB.
Ken

11.04>11.10>12.04 LTS. Yes, you need to go through all the releases. My advice? Backup and do a clean install. Much less problematic. But sounds like you're off and racing already. 

Unsure why you can't boot from USB. Perhaps you should give more detail about that rather than head into potential issues with a double-upgrade. You are going to BIOS and choosing to boot from USB but it is going straight to the hard drive? That would mean the USB is not correct and it is finding nothing to boot there, dongle probably set up wrong. How did you create it?

PS: Keep in mind LTS upgrades to LTS in one shot, for instance 12.04>14.04 LTS is/will be one click in the Update Manager (this has been the case with the LTS releases for awhile).

Good luck.

---

### Post by Kenc3 on 2013-06-14
Since posting this I downloaded the manual and I may have a copy of 12.04 that I downloaded last night on my computer somewhere. I may be able to make a live CD with that one. I have a blank CD now.
 I am going to try that. If it works one of the options is supposed to be to upgrade the old system.
 Nothing is on the system I have now that would be of any value anymore. I have not used that system for years.
Thanks,
Ken

---

### Post by fantab on 2013-06-14
> **Kenc3 said:**
> Since posting this I downloaded the manual and I may have a copy of 12.04 that I downloaded last night on my computer somewhere. I may be able to make a live CD with that one. I have a blank CD now.
 I am going to try that. If it works one of the options is supposed to be to upgrade the old system.
 Nothing is on the system I have now that would be of any value anymore. I have not used that system for years.
Thanks,
Ken

Do a clean and Fresh install of the version of Ubuntu you want. Upgrades can be messy.

---

### Post by oldfred on 2013-06-14
The new versions of Ubuntu are oversize and now do not fit on CDs. I suggest flash drive as it is reusable. 

       [URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]https://help.ubuntu.com/community/Installation/FromUSBStick

      [/URL]
 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

    [URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]
[/URL]

---

### Post by Bucky Ball on 2013-06-14
> **fantab said:**
> Do a clean and Fresh install of the version of Ubuntu you want. Upgrades can be messy.

This. If there is nothing you want/need on the drive, start again with a fresh install of 12.04 LTS. You'll be glad you did. 

If you want some control, hit 'Something Else' at the partitioning section of the install and make the partitions and sizes yourself. oldfred has a better handle on all things install, but a basic setup is:

/ = the OS, 15-20Gb;
/home = personal data, large as you like;
/swap = 2Gb fine.

These mount point are selectable as defaults in the partition section, but you can name your own if you want. Good luck.

---

