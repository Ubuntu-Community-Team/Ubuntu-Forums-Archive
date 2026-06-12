---
title: "New install: cannot install grub or lilo on software raid 5 partition"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by trojanfoe on 2008-03-04
Hi there, I have just put together a PC with 4 x 500GB sata disks in order to build a file/media server and installed Ubuntu 7.10 (amd64) from DVD.  However it's failing during the installation of grub with "grub-install (hd0)" failed.  I tried lilo and the same thing happens.

Each disk is partitioned the same with first partition as primary with boot flag set, and all other (/usr, /var, /home, /data1 and /data2) set as logical with boot flag unset.  Raid-5 is used for every partition (i.e. md0 is sd{a,b,c,d}1, md1 is sd{a,b,c,d}2  etc.).  Swap is between the large partitions (middle of the disk) and is not using raid.

Could someone give me a clue as to where my problem lies?

Cheers,
Andy

---

### Post by dstew on 2008-03-04
My guess is that grub is having a hard time finding its root directory in your RAID. Grub understands filesystem, but I don't think it understands RAIDs. The program grub-install puts the stage1 into the MBR, and stage1.5 into the rest of track0, which usually is not part of any partition. However, grub-install needs to embed into stage1.5 the location of the partiton that contains the grub root directory, with its stage2 file. My guess is that it fails at this step.

One solution is to have an un-RAIDed boot partition that contains grub's stage2 and menu, and the kernel images. Once the kernel is loaded, you have the software that can understand RAIDs. However, then you don't have your kernel RAIDed.

Nowhere in the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html") does it say that grub can boot a RAID directly. However, in the [Fake RAID How-To]("https://help.ubuntu.com/community/FakeRaidHowto") there is some detail on getting grub installed to boot a RAID using the device mapping function of grub. It looks a little tricky, but maybe you can get that to work.

---

### Post by trojanfoe on 2008-03-04
Thanks dstew.  I think the problem might be the use of striped raid (raid-0 and raid-5) as the data is on 4 disks, not 1.  I think if I mirrored the root filesystem usind raid-1 then at least grub could get the complete data from one disk and I would still have my data retention at a very small overhead.

I will try re-partitioning and see where that leads me.

Cheers,
Andy

---

### Post by siouzi on 2008-03-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/175535](https://bugs.launchpad.net/ubuntu/+bug/175535) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi

Have you tried **NOT** setting the **B**ootable flag? This could be a bug in the installer. With some raid configurations (mix words like LVM, raid1, raid5, encryption/LUKS freely) there is no problem. For example, LVM over raid1 install hangs with LILO or GRUB error IF AND ONLY IF a bootable flag is set *somewhere*. Another example is LVM over LUKS over raid1, which works fine (except for some manual editing of crypttab...) with bootable flag set! Go figure.

Recently I did a LVM over raid1 install and got it to work without setting the bootable flag. Kudos to **RoboJ1M**.

I can verify that a setup with one raid**1** device set as ext3 and /boot without bootable flag works. Size should be from 64MB up to 256MB (very safe).

---

### Post by trojanfoe on 2008-03-04
Well just making the root filesystem raid1 rather than raid5 sorted out the problem.

Cheers,
Andy

---

