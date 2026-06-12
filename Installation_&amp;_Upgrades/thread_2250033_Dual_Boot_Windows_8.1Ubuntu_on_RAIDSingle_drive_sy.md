---
title: "Dual Boot Windows 8.1/Ubuntu on RAID/Single drive system"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by Emanuele_Virgillit on 2014-10-26
Hello all,
I have a PC over an AMD platform with the following configuration:
. AMD Athlon II X4 630
. ASRock 990FX Extreme4
. 8GB RAM
. GeForce 8800GS
. 2x500GB Hard disks on RAID0 configuration (1TB) with Windows 8.1 installed
. 1x160GB Hitachi hard disk

I want to make a dual boot within this configuration installing ubuntu on the hitachi separated drive. The problem is the following: Last week i tried to install ubuntu over the RAID0 creating a dedicated partition but i immediately understodd that it could be so difficult so i decided to afford another dedicated drive. Ubuntu installation didn't recognized the raid0 but only the two hard disks as separated 500gb drives. 
Now, i think that even if i try to install it on the hitachi HDD it will continue to not recognize the raid system and the win8.1 installation, so i will not have any dual booting possibility. 
There's a way to solve this? oBvgiusly i just want to make ubuntu detect the win8.1 installation on raid in order to have the grub boot menu at the start and let me choose to boot win8.1 on the raid system or ubuntu in the separated drive.

Just ask me if you need some other information on my configuration and thank all in advance :)

---

### Post by oldfred on 2014-10-26
I do not really know RAID, other than it causes issues with standard desktop installs.

The standard desktop installer does not include RAID nor then the RAID drivers. You can add those after install or use the server install and include the desktop of your choice to end up with the same as Ubuntu, Kubuntu etc install.

You can use gparted on your separate drive, should be able to use Something Else to install to that drive, but be sure to choose to install grub2's boot loader to the MBR of that drive. 
       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)


 Does not recommend "fakeRAID"
[http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/](http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/)
[https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID](https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

