---
title: "Installing Ubuntu from LiveCD on Raid0"
date: 2018-10-01
forum: Installation &amp; Upgrades
---

### Post by aegistitan on 2018-10-01
Hello! 

I've been encountering an issue while installing ubuntu from VirtualBox Live CD on VHD (Virtual hard Disks), after creating 3 drives and 3 partitions, making two of them in raid0 and the 3rd just ext4 for bootsector, after launching installation and selecting the raid as primary in my case md0 and sdd1 for bootloader, the installation runs till end and pops an error that it failed to install grub on sda and sdb even though in installation it was defined that it should be on sdd, any ideas what could be the issue?

---

### Post by oldfred on 2018-10-01
If UEFI, grub only wants to install to ESP on first drive or usually sda.
Change drive order SATA port connections. Make boot file SATA0 or first port so it is then seen as sda.

You could temporarily disconnect drives, but then full install would be on current sdd which then as only drive would become sda.

RAID 0 not normally recommended.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

