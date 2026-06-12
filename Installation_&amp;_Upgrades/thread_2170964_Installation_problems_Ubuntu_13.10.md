---
title: "Installation problems Ubuntu 13.10"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by sonalkeshav95 on 2013-08-28
[FONT=microsoft sans serif][COLOR=#404040]I have been installing Ubuntu since 12.04 and I never had any problems, But every time i try to install Ubuntu 13.10 (Unity/gnome) the installation freezes (sometimes even during the boot itself) and I can't even get to the installation. It also does not connect to wi-fi (ethernet works fine) And the notification bar (which for some reason stretches itself from the top of the screen to the middle). Does this happen to anyone else? and how do I solve this?[/COLOR][/FONT]

---

### Post by grahammechanical on 2013-08-28
This post will soon be moved to the Ubuntu+1 section and there you will find a thread about this problem.

I have seen this issue on Daily Saucy Salamander ISO images. Things like this happen during the development cycle because the installer is also being developed. Since the Saucy daily images were made available I have experienced the install crashing during the copying of files section. The installer claimed that there was not enough disk space although there was 10GB in the partition. Recently, the installer failed to set a file system. Mind you I was trying to install to a btrfs file system and not Ext4. And yet I have two installs of Saucy running on btrfs so it should not be a problem.

You can try one of the other methods of installing.

1) Boot the live DVD/USB and wait until you get the TRY - INSTALL dialog and select INSTALL
2) Boot the live DVD/USB and wait until you get the TRY - INSTALL dialog and select TRY and at the live desktop top click the Install Ubuntu icon
3) At the first purple screen press Enter. At the next screen press Enter to select English as the install language or select another language. At the next screen Select Install Ubuntu or Try Ubuntu and at the live desktop click the Install icon.

One or other may work. This has been my experience with both Raring Raingtail and Saucy Salamander during their development cycles. Things get better as the development cycle nears it ends.

By the way, if the ISO image is very recent it will have the Saucy background images and not the Raring ones that Saucy has had until two days ago.

Regards.

---

### Post by sonalkeshav95 on 2013-08-29
Thanks a lot :) You have been very helpful

---

### Post by bgrau2000 on 2013-12-06
I have had the same problem trying to install Ubuntu 13.10 32bit on my Dell DXP061 - though the AMD 64bit installed fine on my Acer W500 tablet... but not the 32bit on the Dell DXP061...

so I chose to install Linux Mint 16 Petra 32bit instead, and the install went flawless... so will stick with Mint for now... :P

---

