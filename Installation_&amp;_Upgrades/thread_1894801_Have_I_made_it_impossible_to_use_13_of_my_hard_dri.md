---
title: "Have I made it impossible to use 1/3 of my hard drive?"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by lesliek on 2011-12-13
I have an Asus netbook with a single 12GB hard drive. It came with Windows XP pre-installed. I installed Ubuntu 10.04 LTS via Wubi and used it as my default operating system.

My main computer also had Ubuntu 10.04 installed via Wubi. I was having some problems with Ubuntu on that computer and was advised to migrate to a regular Ubuntu 10.04 install. I did that successfully.

I then thought that I should switch to regular Ubuntu 10.04 on the netbook, but that migration wasn’t an option, because there wasn’t enough free space for the migration script to do its work.

I therefore installed Ubuntu 10.04 from the start successfully, but used only 8 of the 12 GB to do so, leaving extant what fdisk -l shows as sda1 and sda2. It says about sda1 that it’s bootable, uses cylinders 1-487 and has filesystem HPFS/NTFS. It says about sda2 that it uses cylinders 488-490 and has filesystem EFI (FAT-12/16/32).

Ubuntu’s on sdb. (I don’t understand why fdisk shows the one hard disk as both sda and sdb. I suppose it’s because of the way I installed Ubuntu.) According to fdisk -l, sdb has sdb1, sdb2 and sdb5. Sdb1: 1-933, filesystem Linux; sdb2: 933-981, filesystem Extended; and sdb3: 933-981 Linux swap / Solaris.

Since the only partition shown as bootable is sda1, I’m assuming that that’s where whatever’s needed to boot into Ubuntu on sdb resides.

I’d like to be able to use the whole 12GB of the hard drive, rather than just 8, but don’t know how to achieve that. I’m afraid I may have made it impossible by the way I installed Ubuntu.

I’d appreciate advice.

Leslie

---

### Post by Rubi1200 on 2011-12-14
Hi,
please post the following information for us:

the results of the [URL="http://ubuntuforums.org/Boot%20info%20script"]boot info script
[/URL]
a screenshot of how GParted sees the drive

---

### Post by lesliek on 2011-12-16
Thanks Rubi1200.

After posting, I kept working on this myself and discovered that on the page that Grub throws up when you boot, there was not only an entry at the top for Ubuntu that worked properly. There was also an entry at the bottom that said "Ubuntu on /dev/sda1". I knew that couldn't be true. I decided to select that entry and see what happened. What happened is that I was taken to the Windows bootloader and was able to boot up in XP.

Now the machine turns out to be dualbooting, Windows XP on 4GB and Ubuntu on 8GB.

I'll keep the machine that way, in case my wife, who uses Windows, needs to use the machine sometime.

Thanks again,

Leslie

---

### Post by Rubi1200 on 2011-12-16
Hi,
glad you were able to find a solution :)

---

