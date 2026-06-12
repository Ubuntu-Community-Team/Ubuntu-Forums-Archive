---
title: "Installing Win 7 to Replace Win XP in an Existing Dual Boot of Win XP and Ubuntu 9.10"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by novicee on 2010-05-22
[B]22 May 10
[/B]
I have Win XP installed on one hard disk drive (HDD1) and Ubuntu 9.10 installed on another hard disk drive (HDD2). Win XP was installed first then Unbuntu 9.10 which set up a dual boot menu.
 

 Win XP will no longer boot because I changed the BIOS setting from IDE to AHCI. The problem this causes is described at [http://forums.pcper.com/showthread.php?t=444831](http://forums.pcper.com/showthread.php?t=444831)  :

 “The problem is that if you installed Windows in IDE mode (ie you didn't use F6 and supply a driver disk), then simply changing the BIOS setting to AHCI mode and rebooting will cause Windows to fail and will require a repair install. Most people have been advising to reinstall Windows if you want AHCI enabled.”
 

 I have read that Win 7 supports AHCI “out of the box” so instead of re-installing Win XP I want to install Win 7 to replace it.
 

 I would like to know in advance what installing Win 7 will do to the dual boot menu ?

---

### Post by wilee-nilee on 2010-05-22
> **novicee said:**
> [B]22 May 10
[/B]
I have Win XP installed on one hard disk drive (HDD1) and Ubuntu 9.10 installed on another hard disk drive (HDD2). Win XP was installed first then Unbuntu 9.10 which set up a dual boot menu.
 

 Win XP will no longer boot because I changed the BIOS setting from IDE to AHCI. The problem this causes is described at [http://forums.pcper.com/showthread.php?t=444831](http://forums.pcper.com/showthread.php?t=444831)  :

 “The problem is that if you installed Windows in IDE mode (ie you didn't use F6 and supply a driver disk), then simply changing the BIOS setting to AHCI mode and rebooting will cause Windows to fail and will require a repair install. Most people have been advising to reinstall Windows if you want AHCI enabled.”
 

 I have read that Win 7 supports AHCI “out of the box” so instead of re-installing Win XP I want to install Win 7 to replace it.
 

 I would like to know in advance what installing Win 7 will do to the dual boot menu ?

The best way to go about this is if you don't care about XP, and grub is your bootloader right now, is to use gparted to delete the XP partition then format it to ntfs with gparted, then install W7 in that partition. You will then have to reinstall grub to the MBR with this help step 11 is what you want.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

Now I am assuming that your using grub2 in the Ubuntu install. Also W7 will install but build 2 partitions a 100mb for boot and the rest for the OS. Building the partition ahead of time confines the W7 install I think to a lotted space to build it's boot and main OS partitions.

I'm surprised the Ubuntu will boot with a changed bios.

---

### Post by novicee on 2010-06-08
**8 Jun 10**

Thanks for the advice re installing Win7.

Since my last post here I have installed Ubuntu 10.04. I have changed my mind about installing Win7 or reverting to Win XP. I won't be doing either because it seems to me that Ubuntu 10.04 is a better OS than either version of Windows. 

I can confirm that Ubuntu 9.10 continued to boot after I changed the BIOS setting to ACHI. It was Win XP that failed to boot.

---

### Post by darkod on 2010-06-08
And I can confirm that win7 maybe supports AHCI out of the box, but you can't switch the setting after win7 is already installed. I just tried few days ago.

Lucid continued booting, but win7 not. Changing the setting back to Native IDE, made both of them boot fine as before.

---

