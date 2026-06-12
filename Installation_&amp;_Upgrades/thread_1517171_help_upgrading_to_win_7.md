---
title: "help upgrading to win 7"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by masterchief0026 on 2010-06-24
i have an hp laptop currently dual booting ubuntu 10.04 and windows xp. i want to install windows 7 on the windows xp partition of the hard drive. to do this do i insert my win 7 disk while running xp and load the installer from there or i need to uninstall ubuntu and then reinstall it after putting win 7 on? or whats the easiest way to put win 7 on without messing up or involving the ubuntu partition?

---

### Post by wilee-nilee on 2010-06-24
> **masterchief0026 said:**
> i have an hp laptop currently dual booting ubuntu 10.04 and windows xp. i want to install windows 7 on the windows xp partition of the hard drive. to do this do i insert my win 7 disk while running xp and load the installer from there or i need to uninstall ubuntu and then reinstall it after putting win 7 on? or whats the easiest way to put win 7 on without messing up or involving the ubuntu partition?

You need to run a ```
sudo fdisk -l
``` so we can see the partition sizes and how many you have. Just copy and paste the command into the Ubuntu terminal.

---

### Post by darkod on 2010-06-24
If you literary want to upgrade from XP to 7, you need to put your win7 dvd in the drive while booted in XP. There should be message asking you if you want to upgrade. You should be able to keep the programs but I'm not sure if there will be compatibility issues.

If you don't mind reinstalling the programs, and if you can copy all the data from the XP partition you need to another disk, you could also boot the computer with the win7 dvd and tell it to install into the XP partition, formatting it. All files there will be wiped and you will have clean install of win7. Just make sure you select the correct partition.

Either way, after installing/upgrading to win7 you will have to reinstall grub2 to the MBR. Make sure you use the 10.04 cd and the instructions for grub2 here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by wilee-nilee on 2010-06-24
> **darkod said:**
> If you literary want to upgrade from XP to 7, you need to put your win7 dvd in the drive while booted in XP. There should be message asking you if you want to upgrade. You should be able to keep the programs but I'm not sure if there will be compatibility issues.

If you don't mind reinstalling the programs, and if you can copy all the data from the XP partition you need to another disk, you could also boot the computer with the win7 dvd and tell it to install into the XP partition, formatting it. All files there will be wiped and you will have clean install of win7. Just make sure you select the correct partition.

Either way, after installing/upgrading to win7 you will have to reinstall grub2 to the MBR. Make sure you use the 10.04 cd and the instructions for grub2 here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

There is no upgrade from XP to W7 it is a fresh install and if run from the live XP will save XP stuff in a old windows file. With not knowing the partition numbers or sizes we should at the least, get this information. 

There are problems at times with key activation with upgrade installs, so booting from a live DVD or from the Live XP will probably cause no problems.

---

