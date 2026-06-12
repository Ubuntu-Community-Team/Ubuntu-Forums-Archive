---
title: "W8 UEFI nonmanageble in HP6 2490oe i7 3770 16 GB RAM, how to proceed?"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by Max Gasman on 2013-05-09
The title describes it, how to manage the settings? I have downloaded a DVD with 12.04.02... Max

---

### Post by Max Gasman on 2013-05-09
...additionally, the HP has now two HDD's: System disk = 1TB and a 2TB partitioned in 150GB +150GB + 1,5TB, waiting for UBUNTU in the first partitioning. The motherboard is Joshua 61.                 Max

---

### Post by darkod on 2013-05-09
If W8 came preinstalled in UEFI with Secure Boot and Fast Boot enabled, I think you first need to go into bios and disable Secure Boot and Fast Boot.
Then make sure when booting the ubuntu cd/usb you do it in uefi mode, not legacy mode. It needs to boot in uefi mode to install uefi dual boot.

I don't use uefi so I don't have more details. Something like this should get you started:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I didn't understand what you wanted to say about the partitioning. First you mention 1TB and 2TB disks, and then you say three times 1.5TB partitions. Just keep in mind that ubuntu doesn't install in ntfs partitions, it needs linux type partitions. So you need unallocated space to create the ubuntu partitions unless you already have some to use.

---

### Post by Max Gasman on 2013-05-09
Thank You!

---

### Post by Max Gasman on 2013-05-09
Thank You, Darko!  First, have to correct your missreading: The 2TB HDD is partitoned in 3 (Three) parts, 150 GIGABITS + 150 GIGABITS + (1500 GIGABITS = 1,5 TERABITS). Keeping track of the decades! The formatting goes in NTFS. I have read [[COLOR=#dd4814]https://help.ubuntu.com/community/UEFI[/COLOR]]("https://help.ubuntu.com/community/UEFI") , but as the "Windows Boot Manager" keeps as a closed block, it can only as a whole, be set on another line below all the USBs'. The "Secure Boot" and the "Fast Boot" can be disabled, but so far I have not enabled "Legacy Support".  The first partition is to be for UBUNTU.  What to do next?  Max

---

### Post by darkod on 2013-05-09
yeah, sorry, misread the TB and GB. But if the disk is taken up by the ntfs partitions, and it looks like it, you can't add the ubuntu partitions. What you could do is delete one of the 150GB partitions and create the root and swap (nad maybe separate /home) in its place. If you think 150GB is enough for your planned ubuntu use.

As far as I have understood, the uefi boot is managed by uefi, so in effect you are not using windows bootloader nor grub2. That's why it's important to boot the ubuntu boot media in the correct mode (uefi), so that it installs the correct files for boot to the correct place (the EFI partition).

---

### Post by Max Gasman on 2013-05-09
Thanks, Darkod!  Originally, the principal was to have just the operation system UBUNTU and its working programs on the first partition, and then all Dokuments and the like on the 1500 GB = 1,5 TERABIT last partitition. If there would have been no formatting conflict, between different operating systems, I could have three (3) different operating systems, and a common big "store" of documents in the last big partition.                                                                                                               Am I now forced to give up this idea and reformatting whole the 2TB HDD and only use it for UBUNTU and a second Linux program?                                                                                                   That would exclude W8 document storage in the last partition on the 2TB HDD as of now?             Max

---

### Post by darkod on 2013-05-09
No, you can leave a big ntfs data partition if you want to. Both windows and ubuntu will be able to read it and write to it.
But you can still consider having separate /home partition (not the 1.5TB data partition) so that settings are kept separately from root. That can help you do clean installs in the future.

---

### Post by oldfred on 2013-05-09
You also have to make sure both drives are partitioned the same partitioning type, gpt or MBR(msdos). If Windows is UEFI booting then that drive is gpt partitioned and then you need to make sure second drive is also gpt. Most partitioning tools still default to MBR(msdos).

       Two Drive UEFI installs
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

Systems only boot from one drive, but if you are putting Ubuntu on a second drive I would make sure to manually partition with a 250 to 300MB efi partition as the first partition on the second drive. You may actually use the Windows drive's efi partition to boot, but with an efi partition on the second drive you can configure it to boot directly. I prefer to make each drive boot without any other drive, so when one drive fails you have another way to boot. If parts of booting are on both drives then both drives always have to work. But good backups are still important.

---

