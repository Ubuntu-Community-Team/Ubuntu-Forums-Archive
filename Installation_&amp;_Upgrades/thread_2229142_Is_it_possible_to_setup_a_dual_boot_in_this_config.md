---
title: "Is it possible to setup a dual boot in this configuration?"
date: 2014-06-11
forum: Installation &amp; Upgrades
---

### Post by Robin_Shrestha on 2014-06-11
Hello folks- 

  I have a desktop with windows 7 & ubuntu in a dual boot setup- I really like this configuration. 

  I recently purchased a new laptop. This laptop has a ~100 gig SSD drive as the primary hard drive & 1 TB secondary hard drive. Right now it only has the preinstalled windows 8 on it. I would like to install the latest distribution of Ubuntu (14.04) alongside windows 8. After reading some things online- I know it is not as simple as it used to be- after reading some installation guides online- I know it is a bit more involved. 

   However, I was wondering is it possible to set up so that the ubuntu partition is on my 1 TB hard drive (and not my SSD) ? The space on my SSD is very precious to me- so I was wondering how would I go about doing this? could anyone point me to a very comprehensive guide?

---

### Post by oldfred on 2014-06-11
Best to do full back ups.
Is all of Windows on SSD? And then hard drive is just data?
Are both drives partitioned as gpt?

Windows 8 will be installed in UEFI mode and that only boots from gpt partitioned drives.
So you need to install Ubuntu in UEFI mode and hard drive has to be gpt. And best to have an efi partition on the hard drive or else Ubuntu will install its boot files into the Windows efi partition. No real issue with it doing that, but I like to configure every drive to boot without any other drive. Or when SSD fails or is corrupted you can boot Ubuntu or when hard drive fails or is corrupted you can boot SSD.

Post this:
sudo parted -l

Many new Windows 8 systems also use Intel SRT which uses RAID and adds to the complexity of an install.
** [FONT=arial][SIZE=1]Two Drive UEFI installs[/SIZE][/FONT]**
[http://ubuntuforums.org/showthread.php?t=2192378](http://ubuntuforums.org/showthread.php?t=2192378)
HP Envy 2 drive install i7 & 2 1TB drives
[http://ubuntuforums.org/showthread.php?t=2175877](http://ubuntuforums.org/showthread.php?t=2175877)
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Dual  Video Intel & nVidia
[http://ubuntuforums.org/showthread.php?t=1994622](http://ubuntuforums.org/showthread.php?t=1994622)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

---

