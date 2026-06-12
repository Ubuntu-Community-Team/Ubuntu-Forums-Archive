---
title: "UEFI Ubuntu on SSS, Windows on HDD?"
date: 2016-01-27
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2016-01-27
On my laptop I have a 25GB SSD and then a HDD of ~300GB. I would like to install Ubuntu on the SSD, 20 GB / and 5 GB /home, and Windows on the HDD.

My latest dual boot was on a single drive on my desktop. I first created a 1GB /boot partition with GParted, then install Ubuntu and then install Windows. After updating grub this worked fine.

Do I need to do anything different for the configuration I would like on my laptop?

---

### Post by oldfred on 2016-01-27
Is HDD internal? Windows only installs to internal drives.

If only 5GB for /home I would keep it inside / (root). That is how I have my SSD configured, but I do not have Windows. I have a large data partition on my HDD mounted at /mnt/data but many folders linked back into /home. When I still ran XP (before SSDs), I also had another data partition formatted NTFS for shared data like Firefox & Thunderbird profiles, photos for Picasa & some data.

But if system is UEFI, be sure to install in UEFI boot mode. Grub always installs to ESP - efi system partition on drive seen as sda. If HDD is sda, then you need to create the ESP on sda before installing Ubuntu on sdb. Not sure with Windows, but old versions always installed BIOS boot loader & boot partition to drive set as boot in BIOS, even if installing to another drive.

Was/is this an Ultrabook? Those had Intel SRT, which looks like RAID from Linux. Older installs had to remove RAID meta-data from drive. Not sure if still required or not.

Some suggest disconnecting other drive, to insure clean install to that drive only.
And be sure to install both systems in UEFI boot mode with gpt partitioning. How you boot install media, UEFI or BIOS is then how it installs.

---

