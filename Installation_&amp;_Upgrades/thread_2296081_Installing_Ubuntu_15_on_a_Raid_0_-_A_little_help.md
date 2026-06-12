---
title: "Installing Ubuntu 15 on a Raid 0 - A little help"
date: 2015-09-23
forum: Installation &amp; Upgrades
---

### Post by Alexander_Paunovsk on 2015-09-23
Hello, I've installed Ubuntu on a Raid 0 disk, but it won't boot.

I followed this guide here [http://askubuntu.com/questions/334012/a-guide-to-install-ubuntu-13-04-using-a-raid-0](http://askubuntu.com/questions/334012/a-guide-to-install-ubuntu-13-04-using-a-raid-0) but it doesn't seem to work.

Here is my BootInfo paste.

[http://paste.ubuntu.com/12530820/](http://paste.ubuntu.com/12530820/)

---

### Post by oldfred on 2015-09-23
I do not know RAID, LMV, not encryption.
But you need to install grub so UEFI knows to use the FAT32 ESP - efi system partition inside your RAID.
Most installs with LVM keep ESP & /boot outside of LVM. I guess it is a bit easier.

[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)
He does not have a separate /boot which you do.
So you need to follow his directions on mounting efi & system & also add one for your /boot. The run the grub install command. If booted in UEFI mode, it should add a entry to UEFI for booting.

What brand/model system. Some do not like ubuntu in UEFI and you have to do a work around which is an additional complication.

You do know RAID 0 is for speed with no backup and risk that if one drive fails you lose all data on both drives.
 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

