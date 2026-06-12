---
title: "Windows 7 refuses to load, and fail recovery"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by francisco2007 on 2013-08-27
When I try to fix it writes the notorious "The version of system recovery option is not compatible with the version of windows you are trying to repair"

Anyways, since I'm using Ubuntu 99% I don't mind reinstalling windows. 

What's the best strategy to do that without jeopardizing my ububtu partion? How do I recover the grub?  (just update-grub from the live-cd? That simple?)

Cheers

---

### Post by Mark Phelps on 2013-08-27
When you go to reinstall Windows from install media (DVD for Win7), during initial setup, it will allow you to select a parition for the install.  Just be sure to select the one currently containing Windows.  It will overwrite that.

But ... it will also overwrite the GRUB code in the MBR of your hard drive, so when you reboot, you will only see Windows.

You would then need to reinstall GRUB from a LiveCD or LiveUSB to get back access to Ubuntu.

---

### Post by francisco2007 on 2013-08-28
OK, thanks. 
I have a UEFI bios. I actually don't remember if it gave me hard time on the initial setup. Does it change anything?

---

### Post by Mark Phelps on 2013-08-28
> Does it change anything? 

Yes ... it does, quite a lot .. and I'm not familiar with UEFI BIOS setups, sorry.

---

### Post by mastablasta on 2013-08-28
about UEFI read more here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2013-08-28
Even with newer hardware/motherboards that were UEFI, most Windows 7 systems were installed in BIOS or CSM - compatibility support mode. Only a few systems with Windows 7 released shortly before Windows 8 used UEFI.

So is your Windows 7 installed in UEFI or BIOS even if hardware is UEFI?

If drive is gpt then it has to be UEFI and you will have an efi partition. IF drive is msdos(MBR) then you are in BIOS mode.

From terminal post this:
sudo parted -l

---

### Post by francisco2007 on 2013-08-29
> **oldfred said:**
> Even with newer hardware/motherboards that were UEFI, most Windows 7 systems were installed in BIOS or CSM - compatibility support mode. Only a few systems with Windows 7 released shortly before Windows 8 
If drive is gpt then it has to be UEFI and you will have an efi partition. IF drive is msdos(MBR) then you are in BIOS mode.

From terminal post this:
sudo parted -l

This is what I got. What do you make of it?

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   992GB   992GB   primary   ntfs
 3      992GB   2000GB  1009GB  extended
 6      992GB   1992GB  1000GB  logical   ext4
 5      1992GB  2000GB  8550MB  logical   linux-swap(v1)

---

### Post by mastablasta on 2013-08-29
look like BIOS to me. but where is the recovery partition?

---

### Post by francisco2007 on 2013-08-29
This is the full report

Model: ATA ST2000DM001-9YN1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   992GB   992GB   primary   ntfs
 3      992GB   2000GB  1009GB  extended
 6      992GB   1992GB  1000GB  logical   ext4
 5      1992GB  2000GB  8550MB  logical   linux-swap(v1)


Model: ATA ST31000333AS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type     File system  Flags
 1      32.3kB  472GB   472GB  primary  ext3
 2      472GB   1000GB  528GB  primary  ntfs


Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4


Model: ATA ST3320620AS (scsi)
Disk /dev/sdd: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  320GB  320GB  primary  ext4

---

### Post by Mark Phelps on 2013-08-29
It looks like sda2 is your Win7 OS install.

You might want to consider a Reinstall of Win7 over itself.  That will leave your data intact.

I would make sure all the other drives are disconnected when you do this.

For more details on how to do this, see the following thread at the Windows 7 Forums:  [=Installation and Setup"]http://www.sevenforums.com/tutorials/3413-repair-install.html?filter[3]=Installation and Setup]("http://www.sevenforums.com/tutorials/3413-repair-install.html?filter[3)

---

### Post by oldfred on 2013-08-29
> Partition Table: msdos

Has to be BIOS based and you just have the standard BIOS type install of a 100MB boot/repair partition and your main install on sda2.

If you cannot repair it then Mark Phelps suggestion may be the only alternative. I might still back up data.
Was repairCD/Flash the same either 32 bit or 64 bit as that should be the only compatibility requirement.

---

