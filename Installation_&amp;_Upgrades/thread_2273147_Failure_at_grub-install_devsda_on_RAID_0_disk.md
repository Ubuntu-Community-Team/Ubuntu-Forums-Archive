---
title: "Failure at grub-install /dev/sda on RAID 0 disk"
date: 2015-04-10
forum: Installation &amp; Upgrades
---

### Post by j0330h on 2015-04-10
Hello,

I tried to install Ubuntu along my Windows 8.1 installation on my RAID 0 SSDs. Installation failed at grub-install /dev/sda/ however, when i try to boot back into Windows I'm greeted with a blank GRUB prompt. Windows 8 recovery drive fails at start up repair and bcdboot repair. And Ubuntu livecd's boot-repair just keeps requesting that I add a repository containing GRUB 2 files and try again no matter what repos I add. Please help.

---

### Post by oldfred on 2015-04-10
What brand/model system?

The desktop installer does not have RAID drivers, only the server installer, which you can then add Desktop.

You have to add RAID drivers and install grub to RAID, not to sda & sdb.
       Acer S7 14.04 & Windows 8.1 RAID
[http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest](http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest)

 acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
Older but procedures should be similar:

 Sony Vaio  - EFI dualboot Ubuntu 12.04 and Windows 8 in Raid0 
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)
      
 RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)
[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)

Also
 Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by j0330h on 2015-04-10
It's a custom Desktop I originally tried to install Ubuntu studio x64 then normal Ubuntu x64. I was actually able to get into Windows 8 for a brief moment using bcdboot C:\Windows after forcing Ubuntu onto the machine with the Install along side option but after cleaning up the partitions grub took over and went into rescue mode and the command no longer works again. I believe the RAID is handled by the BIOS it's a Gigabyte Z77x UP5-TH board.

---

### Post by nerdtron on 2015-04-11
I don't think GRUB supports RAID-0 install.

If I remember correctly, GRUB needs to be installed at least on RAID1

---

### Post by oldfred on 2015-04-11
BIOS RAID is also known as fakeRAID. see links above.
Several users posted that with UEFI they had to create or correct the grub.cfg in the efi partition to be a configfile to the RAID partition. 

With BIOS this worked, not sure with UEFI.
 "fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

 RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)
[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)

---

