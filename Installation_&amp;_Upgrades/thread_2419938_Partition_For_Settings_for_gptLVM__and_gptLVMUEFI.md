---
title: "Partition For Settings for gpt/LVM  and gpt/LVM/UEFI"
date: 2019-05-27
forum: Installation &amp; Upgrades
---

### Post by giobaxx on 2019-05-27
I'm trying to figure out how the minimun partition scheme requiring when i use BIOS or UEFI, MBR or GPT.....and LVM together because i'm really confused. Below i put the Simplest partition scheme combining together MBR,GPT UEFI and LVM
Could you tell me if what i wrote is correct?[B]
 
BIOS+MBR

[/B]
[LIST=1]
[*]swap
[*]/
[/LIST]

[B]BIOS + GPT
[/B]

[LIST=1]
[*]Bios-grub
[*]swap
[*]/
[/LIST]

**UEFI + GPT**


[LIST=1]
[*]EFI boot partition
[*]swap
[*]/
[/LIST]
 
**BIOS + LVM** i need to set  /boot as Standard Partitions to make the linux bootable

     1 /boot   as standard Partition
     2 swap   LVM storage
     3 /         LV Storage  
       

for **BIOS with GPT Disk plus LVM**?   i need just to add the bios-grub partition(to support GPT disk) and the separated standard partition /boot  to let linux to boot?


[LIST=1]
[*]Bios-grub
[*]/boot
[*]swap LVM Storage
[*]/       LVM Storage
[/LIST]

[B]
UEFI + LVM[/B]?  just add the EFI partition to support UEFI and /boot standard partittion to let linux to boot or not?


[LIST=1]
[*]efi
[*]/boot
[*]swap LVM Storage
[*]/       LVM Storage
[/LIST]



Any clarification would be great......Tanks in advance

---

### Post by oldfred on 2019-05-27
Looks familiar. :)
[https://askubuntu.com/questions/1146591/partitioning-scheme-x-ubuntu](https://askubuntu.com/questions/1146591/partitioning-scheme-x-ubuntu)

Are you dual booting?
If so Windows defines which partitioning you must use as it only is MBR with BIOS and only gpt with UEFI.
Ubuntu can be BIOS or UEFI boot on gpt and I recommend gpt for all new or reformatted drives, if not using Windows in the now very old BIOS boot mode. I started converting drives to gpt back in 2010 and now only a couple of now tiny flash drives are still  MBR.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Do not know LVM, but those that do, recommend it. But it really is more for advanced users or servers as it has a lot of features for those users & configurations.

So I am ignoring any MBR configuration.

With gpt you can add both an ESP and a bios_grub, both are small to a drive. I used to always do that, but have now used only UEFI for 5 or 6 years and stopped adding the bios_grub, but it is only 1 or 2MB. 

You do not need swap partition as newer versions now use swap file. If you have a swap partition it will be used and I believe LVM still creates a swap partition inside the LVM.

If a newer user, I would not use LVM for now unless you really want full drive encryption. And then you must create really good backup procedures, immediately.

I would also suggest separating system from data or use a /home. But you have to use Something Else install option to create partitions, or use gparted to create them in advance. You still use Something Else to select (change button) which partition is which. I use 25GB for / & rest for my data partition(s).

More info on UEFI install in link in my signature.

My most recent install to flash drive, but I still have an unused bios_grub on this flash drive.

```
Disk /dev/sdc: 61.9GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name       Flags
 1      1049kB  211MB   210MB   fat32        ESP        boot, esp
 2      211MB   213MB   2097kB               bios_grub
 3      213MB   22.9GB  22.6GB  ext4         mateUSB
 4      22.9GB  61.9GB  39.1GB  ext4         data


```

---

### Post by Dennis N on 2019-05-27
> BIOS + LVM i need to set /boot as Standard Partitions to make the linux bootable

1 /boot as standard Partition
2 swap LVM storage
3 / LV Storage 

Here, you don't need a /boot partition for LVM, just the root logical volume (LV) and one of: swap partition, swap LV,  or swap file in the OS. 

I'm not clear on what you mean by / LV storage?

For your other cases with LVM: BIOS with GPT Disk plus LVM and UEFI + LVM: no /boot partition required.

---

### Post by giobaxx on 2019-05-27
With LV Storage i mean  Logical Volume. Normally we have powerful workstation with two disk and  normally what they asked me to do is using LVM to create partitions. I remember a linux guy that was working mainly with Red Hat told me that /boot cannot be within the LVM configuration and it should be in a separated standard partition to let the system boot. is it not true?

---

### Post by oldfred on 2019-05-27
If you do not want encryption, you can skip that part. But it is LVM install in detail.
[https://help.ubuntu.com/community/ManualFullSystemEncryption/](https://help.ubuntu.com/community/ManualFullSystemEncryption/)
Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) & 
[https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092)

Not sure about Redhat, Ubuntu used to use /boot partition outside LVM, but now you do not have to have it.

---

### Post by giobaxx on 2019-05-27
[COLOR=#c61919]@olfred[/COLOR]

We don't use dual boot, but we have some powerfull workstation that are almost used as server and they need a more advanced configuration. Sometimes they have raid, other times LVM. They use of LVM is not depends on me, unfortunately :-( is a choice of our sys admin.

If i use **LVM** or **RAID** the **biosgrup** and/or** efi** partition must be part of **LVM Volume/RAID** or must be treated as standard partition?

with "*[COLOR=#000000]Not sure about Redhat, Ubuntu used to use /boot partition outside LVM, but now you do not have to have it.[/COLOR]"*  you mean that now we dont need anymore a separate Partition for /boot and i can put inside the LVM
[COLOR=#c61919]
[/COLOR]

---

### Post by Dennis N on 2019-05-27
> **giobaxx said:**
> With LV Storage i mean  Logical Volume. Normally we have powerful workstation with two disk and  normally what they asked me to do is using LVM to create partitions. I remember a linux guy that was working mainly with Red Hat told me that /boot cannot be within the LVM configuration and it should be in a separated standard partition to let the system boot. is it not true?

That may have been correct years ago (before I ever used LVM) but not anymore, at least for unencrypted installs. I can't advise on using it with encryption.

No boot partition here:

```
 Model: ATA Samsung SSD 860 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3146kB  2097kB                     bios_grub
 2      3146kB  44.0GB  44.0GB  ext4
 3      44.0GB  296GB   252GB                      lvm

```

My experience includes Ubuntu (and family), Linux Mint, Fedora, Manjaro and this is true for all of these.

---

### Post by oldfred on 2019-05-27
UEFI cannot read inside LVM, so ESP - efi system partition must be outside the LVM. Same with bios_grub.
Rest I do not know details on LVM, I do not use it and have only seen various installs with it.

LVM Advantages/Disadvantages Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

---

