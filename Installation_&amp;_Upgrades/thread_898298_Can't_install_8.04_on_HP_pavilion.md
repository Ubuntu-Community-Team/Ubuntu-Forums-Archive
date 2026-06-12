---
title: "Can't install 8.04 on HP pavilion"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by xterm on 2008-08-23
Hello

I'm trying to install Ubuntu 8.04 (i386 desktop) on a HP pavilion (AMD64) model no d4685.se -a, prod #RJ121AA-B1U (not a laptop)

If I do a clean install I'm getting an error that the files on CD and harddrive doesn't match. Suggestion to clean CD or replace harddrive. I have tried with two different CD-rom drives and two harddrive. Same result. There is a different file every time I try to install. 

I then went on and tried to install the 7.4 version and this worked without errors. Then I tried to uppgrade to 8.4 but get errors on binutils and nano packets with seams to be broken now. 

I can't remove and re-install packets threw synaptic. I get errors that apt is broken. 

I did a 'launchpad' report (folloed the guide after upgrade) and here is the link to that report. 

[https://bugs.launchpad.net/ubuntu/+source/binutils/+bug/260606](https://bugs.launchpad.net/ubuntu/+source/binutils/+bug/260606)

Anyone got any tips on how to fix this?

//Fredrik

---

### Post by meindian523 on 2008-08-23
Did you check your CD for errors before trying to install?

---

### Post by xterm on 2008-08-23
Yes I did. I also have used this CD on other machines as well. Both before and after trying to install on the HP machine

---

### Post by meindian523 on 2008-08-23
Please post the errors you get.

---

### Post by crypope on 2008-08-23
Try the Ubuntu Live CD if you can to see if your hardware is compatible. That will not use the hard drive. If you still have problems - you may have to get a OEM motherboard (non-HP, non-DELL, non "brand name" with a supported chipset for hard drives.

I had nasty problems in the past with HP/Compaq  desktop systems that had special chipsets for hard drives.  I wasted two days to figure out that some of these systems are build only for Windows. They came pre-installed with Windows and when you try to install Linux you run into these issues.

They do not release chipset specs to open source developers and as a result some of them can't be recongnized properly by Linux drives. You should check the install logs and see if at boot detection time chipsets are recognized properly.

---

### Post by xterm on 2008-08-24
Well, The 8.04 Live CD HardWare Testing reports that nothing is wrong/not recognized correctly. Still not able to install. 

I can however install v7.10 without any trouble. But if I then upgrade to 8.04 I get two broken packetets (binutils and another one)

Another thing is that the monitor that came with my HP Home PC packet (HP w19b) doesn't work at all with Ubuntu (7.10 or 8.04). It freezes and displays all kinds of cykedelic patterns on the screen. My old biewPoint monitor workes fine though. 

I guess HP Pavilion isn't Linux friendly att al. Thinking of sending the hwole packets back and try another one instead...

---

### Post by meindian523 on 2008-08-24
Looks like inappropriate settings for refresh rates.Check the manual for the appropriate refresh rates for your monitor.

---

### Post by xeth_delta on 2008-08-24
> **xterm said:**
> Hello

I'm trying to install Ubuntu 8.04 (i386 desktop) on a HP pavilion (AMD64) model no d4685.se -a, prod #RJ121AA-B1U (not a laptop)

If I do a clean install I'm getting an error that the files on CD and harddrive doesn't match. Suggestion to clean CD or replace harddrive. I have tried with two different CD-rom drives and two harddrive. Same result. There is a different file every time I try to install. 

I then went on and tried to install the 7.4 version and this worked without errors. Then I tried to uppgrade to 8.4 but get errors on binutils and nano packets with seams to be broken now. 

I can't remove and re-install packets threw synaptic. I get errors that apt is broken. 

I did a 'launchpad' report (folloed the guide after upgrade) and here is the link to that report. 

[https://bugs.launchpad.net/ubuntu/+source/binutils/+bug/260606](https://bugs.launchpad.net/ubuntu/+source/binutils/+bug/260606)

Anyone got any tips on how to fix this?

//Fredrik

It has been suggested that you should check the intergrity of the CD, to see if it has been burnt properly. Did you do it as indicated in [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) ?

If that CD does not work and the integrity tests pass, I suggest that you try the alternate CD instead.

About the packages not having been installed properly, you can reinstall the problematic ones:
First update the package list
```
sudo apt-get update
```
then
```
sudo aptitude reinstall package_name
```

The packages are thus downloaded from the internet and they will replace the ones existing on your machine.

---

### Post by xterm on 2008-08-28
I tried to re-install the package but it doesn't help. I don't have the correct error message in front of me but it says that the package is corrupted.

---

### Post by Sef on 2008-08-28
Sometimes, the alternate cd will work where the Live CD fails.  To download the alternate cd, click on the box below the green arrow next to start download.  The alternate cd is a text-based installer, but very easy to install.

---

### Post by xterm on 2008-09-09
The computor (my parents) have been running 7.10 for a week now. I was home last night to get the Internet running. I did a update of 7.10 (not upgrade, just an update) and guess what. Now the computor won't start again... 

It get's stuck on running local boot. Nothing more happens. 

My guess is that something stoped working in some packet between a fresh install of 7.10 and latest upgrade... 

It's getting realy boring. This HP model is NOT Ubuntu friendly... 

I have installed Ubuntu on 7 different computors. I have never expericened so much trouble!

---

### Post by xterm on 2008-10-06
Ok. I gave up. They're back on WinXP now. 

By the way. XP didn't find any hardware on the computor. Not even the network card. So I had to install all drivers manualy. I don't know what HP was thinking when they made this computor...

---

