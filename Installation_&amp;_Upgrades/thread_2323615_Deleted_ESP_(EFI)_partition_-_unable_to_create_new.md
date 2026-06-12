---
title: "Deleted ESP (EFI) partition - unable to create new one"
date: 2016-05-06
forum: Installation &amp; Upgrades
---

### Post by gabriel78 on 2016-05-06
I have an Asus Ultrabook UX32A.
I have a small SDD with 24 GB and a big HDD with 500 GB.
Windows 8 was pre-installed.
I deleted ALL Partitions on both discs (because I though I do not need any of them anymore) and installed Ubuntu 16.04.
I created a small partition at the beginning of the SSD and marked it in the installation process as efi.
On the remaining partition of the SSD, I installed Ubuntu 16.04.
After the installation, I was unable to boot into the new installed Ubuntu 16.04.
I tried boot-repair, but without any luck.

Here is a Boot-Summary of boot-repair (I installed it in the live system. The drive of the livesystem is /dev/sdc/)
[http://paste2.org/b9AmUKjv](http://paste2.org/b9AmUKjv)

Please any help!

---

### Post by ubfan1 on 2016-05-06
But you apparently installed in legacy mode, without a grub-bios partition on a GPT disk, so no boot.  Reinstall in UEFI mode.

---

### Post by oldfred on 2016-05-07
In UEFI mode grub only installs to the ESP on sda. So have an ESP on your hard drive.
But use gpt partitioning on both drives and put just / (root) on SSD. Then use HDD for either /home or large data partition like /mnt/data and link all typical /home folders into /home on SSD.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by oldfred on 2016-05-08
After you create the ESP on sda, then grub will install correctly in UEFI mode.
But you need to boot Boot-Repair in UEFI mode.

---

