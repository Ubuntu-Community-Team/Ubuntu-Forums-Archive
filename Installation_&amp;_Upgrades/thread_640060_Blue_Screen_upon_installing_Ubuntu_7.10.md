---
title: "Blue Screen upon installing Ubuntu 7.10"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by Nick11 on 2007-12-13
Having successfully installed Ubuntu on my laptop, and setting it up with all the bells and whistles Compiz Fusion has to offer, I decided to put Ubuntu on my desktop. I already have the partitions set up on the drive and everything is ready to go.

But, here is the problem, when I click start and install, the bar comes up, and when it is just about to go into the installation OS-like install setup, my monitor gets blue screen that says HDMI, which is my monitor's default input display. The last thing I see is a flashing single bar (which I think is typical for this installation). 

I tried both cd drives, different apic commands and what not with no success. 

I really need some help here... If it helps, my desktop settings are:


Monitor: 24" Westinghouse LCD
GPU: x1950pro 512mb AGP
CD/DVD drives IDE
Asus SK8V Socket 940 mobo
AMD FX-53 (AMD 4000+ equivalent)
400GB SATA 150 7200 RPM HDD

---

### Post by xeth_delta on 2007-12-13
Have you tried installing with the alternate cd?

---

### Post by Nick11 on 2007-12-13
> **xeth_delta said:**
> Have you tried installing with the alternate cd?

No, do you think that will fix the problem? I will try that right away, just in case this doesn't work are there any other possible reasons as to why the regular cd installer does not work?

---

### Post by xeth_delta on 2007-12-13
I think the alternate cd will work. There are cases where the regular cd graphical installation interface has problems with some hardware configurations. I have hit such situations myself and managed to later install using the alternate cd.

Let us know how it goes.

---

### Post by Nick11 on 2007-12-13
Okay, I downloaded the file, burned the ISO, and ran the alternate CD. But, this time right after I select my keyboard manually from the list, it loads some things and then... nothing. After some loading bar, nothing happens, I am just there with a blue screen and a gray command line on the bottom. Nothing is happening after this point what do I do now? =/

It seems that the problem is still apparent with the alternate CD, only this time it does not revert my monitor to the default input screen, instead the installer just stops... Any ideas?

EDIT: I just got an error message saying the integrity of the CD may be the problem, so I am now checking the integrity... Alright after checking the integrity it turns out the installer is somehow corrupt. I must now burn another disc. Be right back ^^

---

### Post by Nick11 on 2007-12-13
Okay, this new CD is corrupt as well. It can't happen twice so there is something going on here. It can't be the burning process since it worked on other live cds and such. So, the only option left is the file I downloaded. 

Here is the specific integrity error I am getting: 

"The ./doc/install/manual/en/ch08s06.html file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted."

Help! =/

EDIT: I am verifying the check sum, it is obviously going to be off. So, which files do I need... Hmmm... Actually the check sum passed, what the? Then it must be something happening either in the burnig process or something is going awry just because of my hardware or something....

---

### Post by Nick11 on 2007-12-14
Success! 

The alternate cd worked perfectly (soon as I got it to burn properly).

The problem was the when I burned the CD the write speed was at 24x. Apparently this write speed caused some file corruption on the disk, ruining its integrity. So, I just burned it at 8x, and everything works fine. Thanks a bunch ^^.

---

### Post by xeth_delta on 2007-12-14
Great! And a good reminder to us that sometimes it is better to write important CDs at lower speeds.

---

