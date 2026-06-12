---
title: "Boot-Repair not properly recognizing partitions"
date: 2015-08-31
forum: Installation &amp; Upgrades
---

### Post by slochower on 2015-08-31
I'm having trouble booting after repeated attempts using boot-repair. I've exhausted my supply of ideas. Any suggestions would be greatly appreciated.

Background: I am working on a machine that had an OEM installation of Windows 8. A long time ago, I shrunk the Windows partition, created a couple ext4 partitions (/dev/sda1-3), installed Ubuntu 15.04 and used the drive without issue. Eventually the drive died and I copied the ext4 partitions to a new drive and disconnected the original. But then I couldn't boot. So I booted off the live USB, installed boot-repair and followed the instructions. First, I created an 100 MB FAT32 partition at the start of the disk with the boot flag (/dev/sda4). That wasn't enough, so then I created a 5 MB unformatted partition with the bios-grub flag after that (/dev/sda5). I think we can ignore /dev/sdb here.

Problem:

1. I boot off the live USB. 
2. Boot Repair doesn't detect my BIOS-Boot partition. 
3. I go into GParted, reset the flags on /dev/sda4 to boot and /dev/sda5 to bios-grub. 
4. Relaunch Boot Repair. Boot Repair says the PC is in EFI mode but no EFI partition was detected.
5. Open GParted and verify that flags and partitions are set correctly.
6. Can't do the "Recommended repair."

URL: [http://paste.ubuntu.com/12239303/](http://paste.ubuntu.com/12239303/)

---

### Post by oldfred on 2015-08-31
I do not understand why Boot-Repair is not seeing your efi partition.
For UEFI boot you need a FAT32 formatted partition with the boot flag if using gparted.
For BIOS boot on gpt partitioned drive you need a 1 or 2MB unformatted partition with the bios_grub flag.
You bios_grub is large, but that should not matter.

Post this, if newer Ubuntu you may have gdisk already or may need to install it:
       sudo apt-get install gdisk
sudo gdisk -l /dev/sda

    
You had an efi partition, but UUID is invalid and now it is commented out. Was this your original ESP - efi system partition?

```
 #UUID=377E-708F	/boot/efi	vfat	defaults	0	1


```

You may want to house clean out some kernels.
And I prefer to give a label to my data partitions and mount them by assigning a mount point, as UUIDs do not mean anything.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by grahammechanical on 2015-08-31
This is what worries me about what you were doing.

1) Grub was in the MBR of the old drive but not in the MBR of the new drive. 
2) Grub looks for its configuration files in /boot/grub/
3) Let us assume that the Grub configuration files are on sda1 in /boot/grub/, then Grub will recognise sda1 by its UUID number (Unversally Unique Identifier).
4) The partitions on the new drive will have different UUIDs to the partitions on the old drive. So, copying the contents of those old partitions to the new partitions would not have changed the recorded UUIDs in the Grub configuration files.

Regards.

---

### Post by slochower on 2015-08-31
Thanks for the reply! This is what gdisk -l /dev/sda spits out:

```

GPT fdisk (gdisk) version 0.8.10

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 7814037168 sectors, 3.6 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 3B347BA3-1BC1-4239-957E-CC2DBB8AB459
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 7789 sectors (3.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1          229376      2048227327   976.6 GiB   8300  
   2      2048229376      2310371327   125.0 GiB   8300  
   3      2310373376      7814035455   2.6 TiB     8300  
   4            2048          217087   105.0 MiB   EF00  
   5          217088          229375   6.0 MiB     EF02  


```

I *think* the commented UUID was the old one, but now that drive is totally disconnected so I don't think I have a way of checking at the moment.

The UUIDs should have mount points, no? Like this:
```

UUID=0d0769df-3845-4e2f-bc5e-ec692f38b59d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb4 during installation

```

Maybe I'm misunderstanding what you're saying.

---

### Post by slochower on 2015-08-31
1) Yup
2) Yup
3) Right...
4) I actually used Copy/Paste in GParted, which *should*, I think, keep the UUIDs. Then I disconnected the original drive so I wouldn't have duplicate UUIDs. I was loosely following this guide: [https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition) but I didn't do the tune2fs commands.

---

### Post by oldfred on 2015-08-31
Did you then not copy the ESP?
And when UUID change you have to totally uninstall/reinstall grub to get it to fully update. And you need to be in the same mode BIOS  or UEFI as original install.
With gpt you are not supposed to copy partitions as gpt partitions have internal GUID that also must match partition table. That may be the issue.

       Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)
Do not use dd with gpt partitions. Whole drive ok if old drive not used anymore, or no duplicates.
But do not use dd for copies from MBR to gpt partitioned drives, can use cp -a
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)
Restore full drive dd backup - resync gpt partition tables and fsck pursuvant
[http://ubuntuforums.org/showthread.php?t=2145563](http://ubuntuforums.org/showthread.php?t=2145563)

Part of reason I normally suggest new clean install and copy /home, apps and/or data into new install.

---

### Post by slochower on 2015-08-31
> **oldfred said:**
> Did you then not copy the ESP?

No, originally I was planning to use the original drive only for the ESP because I know how messy it could get... but I was having trouble booting with the old hard drive attached because it kept reporting bad sectors. So that's when I tried to recreate the ESP partition on the new drive.

> **oldfred said:**
> 
And when UUID change you have to totally uninstall/reinstall grub to get it to fully update. And you need to be in the same mode BIOS  or UEFI as original install.
With gpt you are not supposed to copy partitions as gpt partitions have internal GUID that also must match partition table. That may be the issue.

       Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)
Do not use dd with gpt partitions. Whole drive ok if old drive not used anymore, or no duplicates.
But do not use dd for copies from MBR to gpt partitioned drives, can use cp -a
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)
Restore full drive dd backup - resync gpt partition tables and fsck pursuvant
[http://ubuntuforums.org/showthread.php?t=2145563](http://ubuntuforums.org/showthread.php?t=2145563)

Part of reason I normally suggest new clean install and copy /home, apps and/or data into new install.

Hm, so do you think the only thing to do is to reinstall, format the / partition, and let the installation procedure to rewrite the boot-loader?

---

### Post by oldfred on 2015-08-31
My concern is the the gpt's/GUIDs may be out of sync. Do not know details other than you should not have that, but it can be created by image copy of partitions.

I think one of above threads has commands to resync GUIDs. I might try that first, especially if thinking of reinstalling and it does not matter if something goes wrong.

---

### Post by slochower on 2015-08-31
> **oldfred said:**
> My concern is the the gpt's/GUIDs may be out of sync. Do not know details other than you should not have that, but it can be created by image copy of partitions.

I think one of above threads has commands to resync GUIDs. I might try that first, especially if thinking of reinstalling and it does not matter if something goes wrong.

Hm, yes I think I found the commands in post 3 of this thread [http://ubuntuforums.org/showthread.php?t=2145563](http://ubuntuforums.org/showthread.php?t=2145563). 

```

sudo sgdisk - v /dev/sda
sudo parted /dev/sda 'print'           
sudo fsck /dev/sda2                    

```

Nothing changed. At this point, it may be quicker to try to reinstall / so I can use my machine. During reinstall, should I leave my partition table as it is -- with /dev/sda4 and /dev/sda5 or delete those and the let the installer do its thing? Since I have two data partitions on the drive, I don't want the installer to format the whole drive.

---

### Post by oldfred on 2015-08-31
I would only use manual partitioning then. And make sure you have good backups.
There was a major bug where the auto install option said overwriting just Ubuntu, but it erased entire drive. Many lost Windows or data partitions.

And only versions (ISO) created after all fixes include the fix. So users who use a older version still can have this issue.
 Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions. Perhaps in 15.04.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by slochower on 2015-08-31
Thanks for the tips. I did use "something else" to delete the unformatted BIOS-Boot partition, delete the FAT32 partition, and reformat /. But still no dice. I used the live USB image to run Boot Repair and it complained about the missing BIOS-Boot partition, so I created it in GParted and Boot Repair finished the recommended repair. But I still couldn't boot from the BIOS. So I used the live USB image again, and Boot Repair complained about missing the EFI partition. I create that in GParted, but Boot Repair can't see the EFI partition. Any suggestions? I don't care about UEFI booting and I'd be happy with a legacy solution...

---

### Post by oldfred on 2015-08-31
You have to be consistent.

If you want UEFI boot you must have the ESP - efi system partition.
Or if you want BIOS you must have the bios_grub partition.

If it still cannot see efi partition, I might delete & recreate. If it has any efi files in it back those up first. It must be FAT32 formatted and with boot flag.

Did you run the sgdisk commands?
sudo sgdisk -v /dev/sda

---

### Post by slochower on 2015-09-01
> **oldfred said:**
> You have to be consistent.

If you want UEFI boot you must have the ESP - efi system partition.
Or if you want BIOS you must have the bios_grub partition.



I have been told both things by Boot-Repair, so I've created both partitions.
> **oldfred said:**
> 
If it still cannot see efi partition, I might delete & recreate. If it has any efi files in it back those up first. It must be FAT32 formatted and with boot flag.


Yup. I deleted the EFI partition during the clean install, tried to boot and it wouldn't work. So I launched Boot Repair which told me to recreate it. Boot Repair still can't see the new, blank EFI partition (screenshot attached).

> **oldfred said:**
> 
Did you run the sgdisk commands?
sudo sgdisk -v /dev/sda

Yup. It says no errors.
```

ubuntu@ubuntu:~$ sudo sgdisk -v /dev/sda

No problems found. 2016656378 free sectors (961.6 GiB) available in 4
segments, the largest of which is 2016651264 (961.6 GiB) in size.


```

---

### Post by oldfred on 2015-09-01
Boot-Repair cannot create partitions.
And if it is updating a UEFI install it must see the ESP, or if updating BIOS on gpt partitioned drive, it must see the bios_grub partition.

I still think it may be something related to out of sync GUID, but do not know an easy way to list or compare GUID. I thought deleting & recreating FAT32 partition may fix that?

Do you have efi files in the ESP partition?
If you get errors, run this:
 sudo fsck -t vfat /dev/sda5

---

### Post by slochower on 2015-09-01
> **oldfred said:**
> Boot-Repair cannot create partitions.
And if it is updating a UEFI install it must see the ESP, or if updating BIOS on gpt partitioned drive, it must see the bios_grub partition.

I still think it may be something related to out of sync GUID, but do not know an easy way to list or compare GUID. I thought deleting & recreating FAT32 partition may fix that?
 
Yeah, me too. I don't know why or how, but that didn't do the trick.

> **oldfred said:**
> 
Do you have efi files in the ESP partition?

Not that I know of.
> **oldfred said:**
> 
If you get errors, run this:
 sudo fsck -t vfat /dev/sda5

fsck says that a dirty bit is set and the partition may not have been unmounted properly. I tell it to fix the dirty bit, but when I run fsck again, it says the same message.

---

### Post by oldfred on 2015-09-01
Then delete & recreate it again.

---

### Post by slochower on 2015-09-01
I'm stuck in the cycle. I delete the unformatted bios_grub partition and I delete the boot FAT32 partition. I launch Boot Repair. First it says GPP detected and I have to create the unformatted bios_grub partition. So I do that in GParted and relaunch Boot Repair. Then Boot Repair says I'm missing the FAT32 partition, so I go ahead and create that in GParted and relaunch Boot Repair. Boot Repair still stays it can't find the EFI partition. There's no way out of the loop. This is a really unfortunate position and the only thing left to do is to do a complete reinstall, letting the installer take over the entire disk and restore from backups. Simply reinstalling the / partition didn't work.

---

### Post by oldfred on 2015-09-01
You are booting or repairing in different modes. 
If it is asking for the bios_grub then that is BIOS/CSM mode.
If it is asking for the ESP then that is UEFI mode.
And you need one or the other.

---

### Post by slochower on 2015-09-01
I was using UEFI boot the whole time (though I was willing to forgo that if it would solve the issue). Boot Repair would complain about *both *bios_grub and ESP partitions in the same session -- that is, without rebooting. The cycle I described in post 17 would happen running Boot Repair twice in a row. So I suspect that Boot Repair was just confused. I couldn't spend any more downtime on fixing the issue, so I reinstalled and let the Ubuntu installer take over the disk. I restored my data from backups. For the record, the installer created only the ESP partition, not the bios_grub partition.

---

