---
title: "Removing Linux Mint from dualboot"
date: 2024-08-08
forum: Installation &amp; Upgrades
---

### Post by sports fan Matt on 2024-08-08
If I wanted to remove Linux Mint and only run Noble, I for the life of me can't remember how to wipe that portion of the drive. I dual boot mint and noble at the moment with 128 GB going to Noble and 127 going to Mint (256 GB Hard drive)

---

### Post by yancek on 2024-08-08
If you simply want to use the Mint partition for data from Ubuntu you would just format the Mint partition using gparted or other partition management software.  Do make certain you get the correct drive/partition.  If you still have the media (DVD/USB) you used to install Ubuntu, it has gparted on it and you could use that.  Or you can simply install it on Ubuntu or use fdisk or parted or any partition manager.

Once you have formatted the old Mint partition, you can create another partition there to use for data.  You might run sudo update-grub after the format to remove the Mint entry from the Grub menu.  One thing to take care about it to ensure that the bootloader is from Ubuntu and not Mint before doing anything else you will have problems booting.

---

### Post by sports fan Matt on 2024-08-08
I just used a flashdrive but i turned it into a Ventoy flash drive.  And I could just use the data ~ didn't think about that. Let me install Gparted and see what it says.

---

### Post by sports fan Matt on 2024-08-08
Ok, not exactly sure how to imput :)

---

### Post by sports fan Matt on 2024-08-08
file:///home/mattyice/Pictures/Screenshots/Screenshot%20from%202024-08-08%2015-44-37.png[IMG]file:///home/mattyice/Pictures/Screenshots/Screenshot%20from%202024-08-08%2015-44-37.png[/IMG] maybe that works. [IMG]file:///home/mattyice/Pictures/Screenshots/Screenshot%20from%202024-08-08%2015-44-37.png[/IMG] maybe that works if not let me know :)

---

### Post by grahammechanical on 2024-08-08
I would like to make a point. Which OS is in control of the Grub bootloader? Remove the OS in charge of Grub and you may not be able to boot the remaining OS.

Load into Ubuntu and run the Disks utility and make a note of the partition that contains the boot files. On my system I see

> Contents FAT (32 bit version) mounted at /boot/efi
Device /dev/nvme0n1p1
Partition type EFI System

The EFI System partition is where the boot loader files go. Now run

```
sudo grub-install /dev/xxxx
```

That will put Ubuntu in control of the Grub boot menu. Now when you delete or format that Linux Mint partition you will still be able to boot Ubuntu. Next you load into Ubuntu and run

```
sudo update-grub
```

That will remove Linux Mint from the Grub boot menu. The Linux Mint boot files will still be in the EFI System partition. They can be left or deleted if you can identify them.

Regards

---

### Post by sports fan Matt on 2024-08-08
[IMG]file:///home/mattyice/Pictures/Screenshots/Screenshot%20from%202024-08-08%2016-10-38.png[/IMG] this is from disks.

---

### Post by tea for one on 2024-08-08
> **sports fan Matt said:**
>  maybe that works if not let me know 
No, it doesn't work.
You cannot just provide a path to your own user directory, you have to use the forum [COLOR="#0000FF"]Attachments[/COLOR] method.
Adv Reply > Attachments > Manage Attachments
Picture herewith

P.S. If I could actually see the picture in your user directory, I may be tempted to steal all your money while I'm there ;)

---

### Post by sports fan Matt on 2024-08-08
Ok here we are. the 128 GB volume is the Mint partition.

---

### Post by #&amp;thj^% on 2024-08-08
> **tea for one said:**
> 
P.S. If I could actually see the picture in your user directory, I may be tempted to steal all your money while I'm there ;)

I'll do a 50/50 split with ya....wink wink  :P

---

### Post by sports fan Matt on 2024-08-08
Ya'll wouldn't get much haha #poor.

---

### Post by tea for one on 2024-08-08
> **sports fan Matt said:**
> Ya'll wouldn't get much haha #poor.
Not to worry, I know that 1fallen hides the front door key under the plant pot on the porch........I'm on my way

---

### Post by sports fan Matt on 2024-08-08
haha

---

### Post by #&amp;thj^% on 2024-08-08
It's a good thing  sports fan Matt is such a good sport...:)

---

### Post by sports fan Matt on 2024-08-08
indeed.  I honestly don't think i mucked this up too badly.

---

### Post by sports fan Matt on 2024-08-08
Partition two is the Mint install.

---

### Post by tea for one on 2024-08-08
> **sports fan Matt said:**
> Partition two is the Mint install.
The picture is not very clear.
Partition 2 seems to be 128GB yet in post no.1 you mention that 128GB is noble? 
Also, do you have two EFI partitions i.e. partitions 1 and 3?
Finally, which OS controls Grub?

---

### Post by sports fan Matt on 2024-08-08
I might have two ~ unsure.  i'll screenshot a better picture blown up from disks.

---

### Post by sports fan Matt on 2024-08-08
Hopefully that one is clearer :) ~ I cant make the screenshot any bigger

---

### Post by sports fan Matt on 2024-08-08
One of these is bigger :)

---

### Post by sports fan Matt on 2024-08-08
The 128 GB volume is Mint, which I'd like to allocate to Ubuntu

---

### Post by Dennis N on 2024-08-08
As I see it, you 256 G disk is this:

part 1 - a small bios boot partition - unused by UEFI systems. Is Mint a BIOS install? Since if UEFI, part 2 and 3 would switch places.
part 2 - 128 G Mint
part 3 - an EFI system partition (needed by UEFI)
part 4 - 127 G Ubuntu
no free space

With Ubuntu on part 4, it's bounded by the EFI system partition and the end of the disk so you can't enlarge Ubuntu's root partition. You have to either follow the suggestion for creating a data partition on part 2 given in post #2; or start over and install Ubuntu with the erase and install option and get the maximum space for Ubuntu.

---

### Post by sports fan Matt on 2024-08-09
So this morning, I wiped the system except when I chose Ubuntu to use the whole entire disk, it says it's installed but no such luck.  It kept restarting and "acting " like the Ubuntu install was present.  So I have LM for now, but I have to ask, it is possible the ISO got corrupted in Ventoy?

The strange thing is with Mint being on the disk, it boots immediately.  can' run Ubuntu with Mint, just not standalone.  

Matt

---

### Post by oldfred on 2024-08-09
Instead of screen shots which I cannot see with my old eyes use terminal & post in code tags to preserve formatting. 
[https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)

These show details.
sudo parted -l
lsblk -f

---

### Post by sports fan Matt on 2024-08-09
Model: General USB Flash Disk (scsi)
Disk /dev/sdb: 61.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  61.8GB  61.8GB  primary               boot
 2      61.8GB  61.9GB  33.6MB  primary  fat16        esp


Model: LENSE20256GMSP34MEAT2TA (nvme)
Disk /dev/nvme0n1: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  2097kB  1049kB                                     bios_grub
 2      2097kB  540MB   538MB   fat32        EFI System Partition  boot, esp
 3      540MB   256GB   256GB   ext4

---

### Post by sports fan Matt on 2024-08-09
NAME FSTYPE FSVER LABEL   UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
sda                                                                           
sdb                                                                           
&#9500;&#9472;sdb1
&#9474;    exfat  1.0   Ventoy  4E21-0000                              51.9G    10% /media/mattyice/Ventoy
&#9492;&#9472;sdb2
     vfat   FAT16 VTOYEFI 223C-F3F8                                           
nvme0n1
                                                                              
&#9500;&#9472;nvme0n1p1
&#9474;                                                                             
&#9500;&#9472;nvme0n1p2
&#9474;    vfat   FAT32         26F3-E861                             505.8M     1% /boot/efi
&#9492;&#9472;nvme0n1p3
     ext4   1.0           ada6ed06-41cb-4641-9a28-b84348891767  205.9G     7% /

---

### Post by sports fan Matt on 2024-08-09
Now I reinstalled mint this morning to just get something working, but if I erase and use "whole disk, it restarts in a loop" Could Ventoy be the issue?

---

### Post by oldfred on 2024-08-09
You show both a bios_grub partition for BIOS boot and an ESP - efi system partition for UEFI boot.
You have to always be consistent and generally if UEFI system, better to install in UEFI boot mode to gpt partitioned drives.

But default boot setting in UEFI settings must match how you install.
And how you boot install media is separate and must match how you want to boot.
So make sure UEFI/BIOS is set for UEFI boot. And always boot USB flash drive in UEFI boot mode.

If  you have a grub installed in BIOS mode & system tried to boot that when last install was UEFI, it will not boot, or boot to grub>.

If you have install and want to know details you can always run Boot-Repair's Summary Report and post link.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by sports fan Matt on 2024-08-09
> [https://paste.ubuntu.com/p/BkXc5TrrkB/]("https://paste.ubuntu.com/p/BkXc5TrrkB/") Hope that works :)

---

### Post by sports fan Matt on 2024-08-09
I have reinstalled pretty close to where I was. Thank you all for the advice. I’m going to see which operating system I want to keep and then go from there in a week. :)

---

### Post by oldfred on 2024-08-09
Because your fstab shows mount of ESP, you must be configured for UEFI boot.
But you have an old grub installed to MBR, which then if you try to boot in old BIOS/Legacy mode, will not work.

Since Mint is an unoffical flavor, not directly supported here. There is a separate sub-forum for Mint help.
But Mint uses "ubuntu" as its UEFI boot entry.
So last install typically overwrites ubuntu entry and becomes default.
If last install is not prefered default boot, you should be able to boot into preferred install & just reinstall grub to make that install default.

---

### Post by sports fan Matt on 2024-08-09
I restored GRUB and now show the two operating systems.

---

