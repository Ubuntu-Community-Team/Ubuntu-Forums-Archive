---
title: "Windows 8 does not recognize ubuntu 10.10 installation just done alongside"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by svrnmnd on 2012-12-29
So I just got a new Asus U47A laptop running windows 8. I booted a live cd of Blackbuntu which is just a 64bit ubuntu 10.10 release with some pentesting tools cooked in.

Booting live had no problems except there was no wireless drivers, and it installed along the windows 8 partition on the data partition (there are 2 recovery partitions, a boot partition, the system partition, and the data partition) Then after install there was the blackbuntu partition added with a linux swapfs partition and another boot partition with grub2.

But when the installation finished and I restarted instead of getting a grub menu it just booted into windows 8 like nothing happened. I ran ubuntu secure remix and ran boot-repair and I got some message that said add repository that has UEFI to the ubuntu 10.10 partition on sda8 or something..then I got a print out for you all to look at

[http://paste.ubuntu.com/1475426](http://paste.ubuntu.com/1475426)

I just want to be able to boot the grub and have it recognize win8 and any other distro I install.

---

### Post by darkod on 2012-12-29
1. Why would you use 10.10 which is not supported any more?

2. Your computer comes with UEFI boot, not the older legacy boot. For dual boot you need to install ubuntu also in uefi mode, not in the legacy mode as you did. Read this carefully:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I suggest using LTS versions, the latest is 12.04 LTS. Which version you choose is up to you, just don't use unsupported versions.

---

### Post by oldfred on 2012-12-29
Only the new 12.10 64 bit version of Ubuntu works with Windows secure boot. Actually it is the new grub2 2.00 which is also supposed to be added to 12.04 with the next point release in Jan. The 12.04 has grub2 1.99 which will boot UEFI but not with secure boot systems.

        The State Of Linux Distributions Handling Secure Boot Dec 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

            You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings or you may have issues getting back into UEFI/BIOS.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
    

Another Asus, but different model that worked.
       Asus S46CA Ultrabook Problems with Windows Recovery and grub after dual-boot install with Ubuntu 12.04
[http://ubuntuforums.org/showthread.php?t=2098477](http://ubuntuforums.org/showthread.php?t=2098477)
> UEFI boot - In order to get into Windows Recovery, I had to hit F9 before GRUB appeared. My mistake was to wait for GRUB to appear, select one of the 2 working Windows options (Windows UEFI loader or Windows Boot UEFI bootx64.efi.bkp) and by that time I was past the possibility to get into Windows recovery system.

---

### Post by Topsiho on 2012-12-29
From the Blackbuntu site:

Blackbuntu is Ubuntu base distro for Penetration Testing with GNOME Desktop Environment. It's currently being built using the Ubuntu 10.10.

Topsiho

---

### Post by svrnmnd on 2012-12-30
> **darkod said:**
> 1. Why would you use 10.10 which is not supported any more?





I love blackbuntu, it is sleek and and has more useful tools than the backtrack 5 r3...If I could port it out..I know I can VM it but....damnit....

Should I live boot into the secure remix then use the boot tools and 'un-install OS' ? because when I installed alongside win 8 it created 3 new partitions like I said; a boot partition with grub, the linux swap partition, and the os partition....should I just delete them, then resize using parted magic? or would it be better to use the secure remix tool?

---

### Post by darkod on 2012-12-30
You can do what ever you want, just make sure you don't mess it up more than it already is.

If you do have secure boot enabled and 12.10 64bit is the only working with secure boot, when installing it select the manual partitioning (Something Else), and just reuse the root and swap partitions that exist. You don't need the small bios_grub partition. Note that ubuntu DOES NOT reuse partitions automatically to prevent accidental data loss. You have to tell it which partition to use as what by selecting it from the list and clicking the Change button.

And in any case you will have to make sure you boot the ubuntu cd in UEFI mode this time, as already mentioned. That is VERY IMPORTANT for uefi dual boot.

Or you can simply delete the three linux partitions and let the ubuntu installer use that space automatically.

---

