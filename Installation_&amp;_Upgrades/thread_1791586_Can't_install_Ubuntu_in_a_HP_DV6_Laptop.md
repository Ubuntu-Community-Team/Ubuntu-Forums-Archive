---
title: "Can't install Ubuntu in a HP DV6 Laptop"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by EApubudu on 2011-06-27
[COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#333333][FONT=Ubuntu Beta]I just bought an HP DV6 6011tx ([[COLOR=#DD4814]link[/COLOR]]("http://h10025.www1.hp.com/ewfrf/wc/product?product=5075390&lc=en&cc=sg&dlc=en&lang=en&tmp_track_link=ot_we/prodlink/en_sg/5075390/loc:0&cc=sg")) Laptop... I formatted the disk through Windows and prepared for installing Ubuntu... When I insert the live CD, it shows the ubuntu start screen and then everything goes black (no cursor... Just like the screen is switched off (but the system is working))

When i try to install from the USB, it says Live media is not found! Some times it also give a black screen like the CD... Have any idea how to fix this?
Thanks
[/FONT][/COLOR][/LEFT]
[/FONT][/COLOR]

---

### Post by Quackers on 2011-06-27
Welcome to UF :-)
What graphics card are you using? You may need to use a boot option (like nomodeset) to boot from the cd.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Also if you get it to boot open up gparted from the live desktop and look to see how many primary partitions are in use already! 4 is the maximum and HP have a tendency to use them all! One will need to be deleted before Ubuntu can be installed, if that is the case.

---

### Post by EApubudu on 2011-06-27
> **Quackers said:**
> Welcome to UF :-)
What graphics card are you using? You may need to use a boot option (like nomodeset) to boot from the cd.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Also if you get it to boot open up gparted from the live desktop and look to see how many primary partitions are in use already! 4 is the maximum and HP have a tendency to use them all! One will need to be deleted before Ubuntu can be installed, if that is the case.

Hi..

My VGA is ATI Radeon HD 6770M... I have already removed the HP Tools partition and made extra partitions for Linux!

---

### Post by EApubudu on 2011-06-27
Hi... I just tried to install with nomodset... Now it give the following errors :

bad lun
bad target number ()this error is repeated several times!

---

### Post by Quackers on 2011-06-27
Is this when booting from the live cd?
When booting, at the first purple screen (with the little man icon at the bottom) press any key. Then choose your language and on the next screen select "check for errors". If any errors are reported the image needs to be burned again - try the slowest settings.
That is, of course, assuming that the md5sum of the downloaded iso is correct.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by EApubudu on 2011-06-27
> **Quackers said:**
> Is this when booting from the live cd?
When booting, at the first purple screen (with the little man icon at the bottom) press any key. Then choose your language and on the next screen select "check for errors". If any errors are reported the image needs to be burned again - try the slowest settings.
That is, of course, assuming that the md5sum of the downloaded iso is correct.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Checked the CD and it says no errors found!

Even checked the downloaded iso... The hashes are the same!

---

### Post by Mark Phelps on 2011-06-28
According to the info in the link you supplied, it looks like your laptop is configure with switchable graphics, that is, it has on-board Intel graphics and can be set to use the AMD graphics instead.

LOTS of folks have posted here with similar machines, and the problem they ran into is that they had to disable the onboard Intel graphics to do the installation (so it would see the AMD card) -- but there was no way in their BIOS to do that.

If your is the same situation, then you're stuck.  Without being able to disable the Intel graphics, there appears to be no way to continue the install.

---

### Post by DrWolfe on 2011-06-30
> **Mark Phelps said:**
> According to the info in the link you supplied, it looks like your laptop is configure with switchable graphics, that is, it has on-board Intel graphics and can be set to use the AMD graphics instead.

LOTS of folks have posted here with similar machines, and the problem they ran into is that they had to disable the onboard Intel graphics to do the installation (so it would see the AMD card) -- but there was no way in their BIOS to do that.

If your is the same situation, then you're stuck.  Without being able to disable the Intel graphics, there appears to be no way to continue the install.

Well this sucks, can this be addressed in the next release of ubuntu?

---

### Post by runiner on 2011-08-06
Have the same issue.

Try to boot with "acpi=off" kernel option.

If success

try to install different kernel. version 3.0 solves problem for me.

Look here [http://linuxpoison.blogspot.com/2011/08/how-to-install-latest-kernel-30-on.html](http://linuxpoison.blogspot.com/2011/08/how-to-install-latest-kernel-30-on.html) for installation instructions

---

### Post by steve11911 on 2011-08-07
Maybe some fresh hope here:

[http://www.tonymacx86.com/viewtopic.php?f=34&t=18470&start=30](http://www.tonymacx86.com/viewtopic.php?f=34&t=18470&start=30)

---

