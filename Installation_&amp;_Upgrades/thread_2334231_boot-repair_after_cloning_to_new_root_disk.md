---
title: "boot-repair after cloning to new root disk"
date: 2016-08-17
forum: Installation &amp; Upgrades
---

### Post by rbroman on 2016-08-17
I have an AMD box, Asus Sabertooth 990FX mobo (uses UEFI BIOS; no legacy mode), Kubuntu 16.04, root disk was/is a GPT partitioned SSD(s). I cloned the old Patriot Pyro 120 GB SSD to a new Samsung 850 Pro 512 SSD using the latest Clonezilla live DVD. Wouldn't boot new SSD. 

So I booted from the Kubuntu 16.04 Live DVD and did the following: Although the old SSD had only two partitions and booted fine, running the bootinfo script on the new SSD said I needed a BIOS boot partition on it. Thus I used gparted to create 2 MB space at the front of the new SSD, by compressing the old / partition, then fixed the partition order so that the new partition was partition 1, and set that partition as the BIOS boot partition. Thus the new SSD (/dev/sdc) now has three partitions: 1 = "BIOS boot", 2 = "/", 3 = "swap". I then ran boot-repair, and set the new SSD as the first boot option in the BIOS. Still no boot from the new SSD - system restarts repeatedly without booting.

The boot-repair output is at [http://paste2.org/yGMbM8NM](http://paste2.org/yGMbM8NM).  It says "Boot successfully repaired", tho I do spot some messages 

mount: mount /dev/sdc1 on /mnt/boot-sav/sdc1 failed: Structure needs cleaning
    mount /dev/sdc1 : Error code 32

fsck -fyM /dev/sdc1
ext2fs_check_desc: Corrupt group descriptor: bad block for block bitmap
.
(stuff fixed but I'm not positive it's totally successful)
.
./dev/sdc1: ***** FILE SYSTEM WAS MODIFIED *****    /dev/sdc1: 11/256 files (0.0% non-contiguous), 47/2048 blocks

Although I'm not a newbie, I must admit I'm a bit confused about grub booting. Why did my old SSD boot with only two partitions (/ and swap), and did I really need a third BIOS boot partition on the new SSD? Does Grub install on the BIOS boot partition, the / partition, or both, and what needs to install where? 

And ..... I'd appreciate recommendations how to diagnose and fix booting on my new SSD.         Thanks!

---

### Post by yancek on 2016-08-17
> Why did my old SSD boot with only two partitions (/ and swap), and did I really need a third BIOS boot partition 

A BIOS boot partition is used if the drive is GPT and not using UEFI.  You have Grub installed in the MBR of all three hard drives but only sdc is shown as a GPT drive.  Do you have sdc set to first boot priority?

---

### Post by oldfred on 2016-08-17
Grub default install is always to sda. And with UEFI it only installs to sda's ESP - efi system partition.
If you do not have an ESP on sda, it will not install.

Or if BIOS boot, you can in Something Else specify grub to install to MBR of any drive. 
But if gpt and BIOS, you must have the bios_grub partition for it to install correctly to any gpt partitioned drive's MBR.

Boot-Repair's default fix with BIOS is to install grub to the MBR of every drive. But if trying to install to MBR of gpt drive then that install fails, even if installed to another MBR(msdos) partitioned drive.

You also show a boot flag on sdc2. A boot flag with gpt partitioned drives means it is the ESP and UEFI will try to find .efi boot files. It is different than the boot flag with MBR partitioned drives where boot flag means to find more Windows boot files. Grub does not use boot flag, but some BIOS/UEFI want to see a boot flag on one partition.
You must remove boot flag from sdc2, use gparted or Disks. System should then boot in BIOS mode if you specify sdc drive.

Moving start of sdc2 partition to insert bios_grub may have corrupted it, so fsck may fix it? 
Best not to move start of partitions unless absolutely required. And grub finds a bios_grub anywhere on drive.
UEFI does suggest that ESP be first on drive, but Windows makes it second or even third partition, but often near start of drive.

---

### Post by rbroman on 2016-08-17
Booted Kubuntu 16.04 Live DVD, then: 
-Using gparted, removed the BIOS boot partition from sdc, since I'm using UEFI and GPT
-Expanded the / partition back into the previous BIOS boot partition, fixed the partition order with fdisk, and fsck'd sdc (clean)
-Set boot flags boot, esp on sdc1 (/ partition)
-Ran boot-repair, specifying place GRUB on sdc only

Now I get "GPT detected, please create a boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed using tools such as gparted. Then try again"

But since I'm using UEFI/GPT, I thought I didn't need that partition??

---

### Post by oldfred on 2016-08-17
No, you need either an ESP or a bios_grub with gpt partitioning.
The ESP generally is near beginning of drive for UEFI boot.
But bios_grub can be anywhere on drive for BIOS boot.

Just add 1 or 2 MB unformatted partition with bios_grub flag, anywhere on drive.

You do not have bios_grub with MBR partitioning. And normally do not have ESP with MBR, although installer usually is FAT32 formatted on MBR partitioned drive and can boot either BIOS or UEFI.

I normally add both ESP & bios_grub to every new or totally erased/reformatted drive as first two partitions. And only now use gpt partitioning. Then I can configure drive either as UEFI or BIOS boot, but normally only use one or the other.

---

### Post by rbroman on 2016-08-17
[COLOR=#000000]Just to repeat, this is a UEFI system (there is no legacy boot option), with GPT. I disconnected all drives except the root drive, which is now sda. So the root disk now has sda1 (EFI system, Fat32, flags boot, ESP), sda2 (/) and sda3 (swap). I fsck'd sda1 and sda2. When I run boot-repair I still get:

 "GPT detected, please create a boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed using tools such as gparted. Then try again"

The bootinfo file for the system configured as above is at [/COLOR]http://paste2.org/ZH0VY0tW[COLOR=#000000]
[/COLOR]

---

### Post by oldfred on 2016-08-18
If Boot-Repair wants the bios_grub partition, you have booted it or live installer in BIOS mode, so it is now trying to install grub in BIOS boot mode.
Best to reboot installer in UEFI mode, and add Boot-Repair. You may be able in Advanced mode to tell Boot-Repair to install the grub-efi-amd64 for UEFI boot.

You show grub installed in gpt's protective MBR for BIOS boot and another grub installed to the partition boot sector (PBR). You should never install BIOS based grub to a PBR, just to MBR. 
But for UEFI boot you specify drive like sda, but grub's efi files for booting are installed in /EFI/ubuntu in the ESP.

Your ESP is not particularly large, but should work. I normally suggest 300MB, Windows creates 100MB normally with 512 sector drives

---

### Post by rbroman on 2016-08-18
I downloaded the [boot-repair-disk-64bit.iso]("http://heanet.dl.sourceforge.net/project/boot-repair-cd/boot-repair-disk-64bit.iso") and created a bootable USB stick using Rufus on a Win10 PC. I used GPT partition scheme and UEFI system type. Booted the stick (as a UEFI USB) on the Kubuntu box, and ran boot-repair. Received same message regards ... "create partition .... bios_grub flag" as before. My latest bootinfo is now in [http://paste.ubuntu.com/23067882/](http://paste.ubuntu.com/23067882/). I do see some errors in there, but don't understand their meaning or how to correct them. 

[COLOR=#000000]Regards "You show grub installed in gpt's protective MBR for BIOS boot and another grub installed to the partition boot sector (PBR). You should never install BIOS based grub to a PBR, just to MBR." .... I assume that's because of my previous attempts at boot-repair, but I don't know how to correct this.

[/COLOR][COLOR=#000000]Regards "You may be able in Advanced mode to tell Boot-Repair to install the grub-efi-amd64 for UEFI boot." ...... I was unable for find such an option, even in Advanced mode.

[/COLOR][COLOR=#000000](Later edit ..... I ran the bootinfo script on my original SSD, and the output is at [/COLOR]http://paste.ubuntu.com/23067985/). When comparing output for the two disks, the original boot disk (which booted fine) had two partitions, and grub was installed  in the MBR of the disk, while the new disk now has the additional EFS partition at the front of the disk, and grub is installed both in the MBR and the second (/) partition. On the new disk, I notice grub on the MBR cannot find core.img. I assume the two grub's on the new disk result from my several runs of boot-repair, including runs when I had a bios_grub partition (and not an EFS partition). 

[COLOR=#000000]I seem to recall, but cannot now find the reference, that grub has some workaround such that it does not need a separate EFS partition, which would account for why the original disk worked with only two partitions (/ and swap). It's possible that the "two grubs" on the new disk are the reason why I can't run boot-repair without getting stopped by the [/COLOR]"create partition .... bios_grub flag" error, and that the failure to boot the new disk is because the grub on the MBR has the error indicated in the preceding paragraph. But I don't know how to fix these problems.)[COLOR=#000000]


[/COLOR]

---

### Post by oldfred on 2016-08-18
Even though you show sda1 as FAT32 with boot flag, so partition info shows it as the ESP - efi system partition, Boot-Repair says it cannot see it.
Sometimes the FAT32 partition just needs chkdsk from Windows or a dosfsck from Linux.

 Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

And occasionally we have seen where a user had to fully backup partition, delete it, recreate it, and then restore the folders & files for UEFI boot.

But I have not seen an ESP as small as yours, so that may also be an issue. Did you manually create that ESP? Installer would have made a larger partition.

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
I normally recommend 300MB unless a full install on smaller flash drive (16 or 32GB), then 100MB.

---

### Post by rbroman on 2016-08-18
Hi Fred: apparently you were replying at the same time I was amending my earlier today post. Can you look at my "Later edit" in parens, and see if it changes things. Thanks, oldrandy

Edit: I gave up and reinstalled Kubuntu 16.04 on the new SSD. The new SSD does boot the system, and it has the same two partitions as the old SSD. I haven't had time to check anything else.

---

