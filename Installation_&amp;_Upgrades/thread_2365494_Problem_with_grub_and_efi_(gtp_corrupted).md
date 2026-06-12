---
title: "Problem with grub and efi (gtp corrupted?)"
date: 2017-07-07
forum: Installation &amp; Upgrades
---

### Post by baloth89 on 2017-07-07
Hi there, i made a mess and i hope to find help here. I've installed ubuntu in dual boot with windows 10 (windows 8 upgraded with 10), then i found problem booting windows so I've used an old version of rescatux to solve problem with windows. In particular i've used the repair mbr choise. After that grub couldn't start too. I tried to use boot repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) (as explained here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)) without any result. I found that my system use gtp/UEFI so maybe i've installed an mbr on efi partition. Now bios could't see any partition also in legacy mode.
this is what i've with command 

sudo fdisk -l
________________________________________________

Disk /dev/loop0: 1.5 GiB, 1553670144 bytes, 3034512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: D1DBA00B-6A7D-4FCD-9B2F-69EF23B05307

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    2050047    2048000  1000M Windows recovery environment
/dev/sda2     2050048    2582527     532480   260M EFI System
/dev/sda3     2582528    4630527    2048000  1000M Lenovo boot partition
/dev/sda4     4630528    4892671     262144   128M Microsoft reserved
/dev/sda5     4892672 1250229336 1245336665 593.8G Microsoft basic data
/dev/sda6  1867972608 1920401407   52428800    25G Microsoft basic data
/dev/sda7  1920401408 1953523711   33122304  15.8G Windows recovery environment
/dev/sda8  1250230272 1867972607  617742336 294.6G Linux filesystem

Partition table entries are not in disk order.


Disk /dev/sdb: 7.5 GiB, 8019509248 bytes, 15663104 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000bf7c3

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *       18 15663103 15663086  7.5G  c W95 FAT32 (LBA)
________________________________________________
i've disabled secure boot. BIOS boot menu shows only network startup. I've tried to start system in legacy mode too but it doesn't want to start.
I can mount EFI partition (sda2) but I don't know what to search. Now i'm using flash version of ubuntu 17.04.
Thank you very much for your attention for this matter. I really appreciate any advice. Ask me for any information you need, I hope you can help me.

---

### Post by oldfred on 2017-07-07
Do not mix UEFI & BIOS/Legacy/CSM. 
You have UEFI hardware & UEFI installs. Trying to do anything with Legacy will just add to problems.

So always boot in UEFI mode and make sure you boot flash drive in UEFI mode. Selection of UEFI or BIOS for flash drive is usually just which of two options to boot flash drive you use.

Even if you tried to install grub in CSM mode, as long as you have UEFI set to boot in UEFI mode, a grub in the gpt protective MBR will never be used.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

What brand/model system?
Some violate UEFI spec that says NOT to use description as part of boot. And only valid description is "Windows Boot Manager". But several work arounds, depending on configuration. (see link below in my signature if you want to read ahead).

Just run the summary report, the auto fix sometimes can create more issues. And be sure to boot in UEFI mode. And post link it gives for report. A few have had issues with no valid link, if that manually post to a pastebin site as often too long to post directly. Use the ppa version to install into your Ubuntu live installer, do not download its ISO as now older.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use second option:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by baloth89 on 2017-07-07
Hi, thank you very much for your advice. I'm using a Lenovo y50-70
and this is the summary pastebin:
[URL="https://pastebin.com/zLBiWeYG"]https://pastebin.com/zLBiWeYG
[/URL]
i'm using flash drive in UEFI mode.

---

### Post by oldfred on 2017-07-07
You have lilo boot loader in protective MBR. That is a Windows type BIOS boot loader. Will never be used, but ok just to leave it. Just do not try to boot in BIOS/CSM/Legacy mode.

Report is not showing grub.cfg, nor fstab and says no kernel in /mnt/boot. But you do have /EFI/ubuntu for UEFI boot and that is normally the last part of an install.

Not sure if a full reinstall of grub using Boot-Repairs advanced mode to totally uninstall/reinstall grub and also check install latest kernel will resolve all the issues, or if a new install would be easier/better.
You can try the Boot-Repair advanced mode fixes.
Or if then you need a full reinstall, be sure to use Something Else and choose existing / (root) partition for new / partition.

See also link in my signature.

---

### Post by baloth89 on 2017-07-07
Thank you for your precious time. i've tried to use Boot-Repairs advanced mode to totally uninstall/reinstall grub without any luck. Should i reinstall it?

---

### Post by oldfred on 2017-07-07
If new install, then that would probably be easiest solution.
If you have any data in /home, then back that up before reinstalling.
And you should always have Windows well backed up, normally (not its recover partitions on same drive) but make sure that is up to date.

---

### Post by baloth89 on 2017-07-08
I'm sorry, just a question, can i use the option: "delete ubuntu 17.04 and reinstal"?

---

### Post by oldfred on 2017-07-09
If that is one of the auto install options, I prefer not to use it.
With Something Else you have control over which partitions you use, but still have to know which partition is which. I have installed to wrong partition.

---

