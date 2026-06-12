---
title: "Help! Problem after installing an operating system next to an existing system Help!"
date: 2018-01-21
forum: Installation &amp; Upgrades
---

### Post by lionel4anlominus on 2018-01-21
Problem after installing an operating system next to an existing system (Help!)

So I had an operating system of Microsoft Windows 10 on a 500GB disk,
And in addition, Ubuntu 17.10 is about 120 gigabytes, and after I deleted the Windows 10,
And installed Ubuntu next to the old Ubuntu, I lost track of the old Ubuntu.

It was encrypted and I can not access it from the new.
;)
Has anyone encountered this? And passed it ..?
:p
Thanks in advance for helpers!

---

### Post by slickymaster on 2018-01-21
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by lionel4anlominus on 2018-01-21
thanks man!

---

### Post by lionel4anlominus on 2018-01-21
Bump

---

### Post by oldfred on 2018-01-22
I do not know encryption.
Was this a manually configured LVM with encryption type install or an encrypted /home?
Normally LVM default erases entire drive.

Post this:
sudo parted -l

---

### Post by lionel4anlominus on 2018-01-22
> **oldfred said:**
> I do not know encryption.
Was this a manually configured LVM with encryption type install or an encrypted /home?
Normally LVM default erases entire drive.

Post this:
sudo parted -l


It with Normally LVM default erases entire drive.
```

[sudo] password for lionel: 
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
 2      538MB   1305MB  768MB  ext4
 3      1305MB  512GB   511GB




Model: ATA KINGSTON RBU-SMS (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
 2      538MB   1305MB  768MB  ext4
 3      1305MB  128GB   127GB




Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 16.8GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  16.8GB  16.8GB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 16.8GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  16.8GB  16.8GB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 494GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system  Flags
 1      0.00B  494GB  494GB  ext4




Error: /dev/mapper/sda3_crypt: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/sda3_crypt: 511GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:
```

---

### Post by oldfred on 2018-01-22
If you erased entire drive what do you want to recover. 
With encryption, the entire idea is that data is not recoverable. You have to restore from backups.
But if you have old partition/volumes and passphrase it may be mountable and data recovered.

---

### Post by lionel4anlominus on 2018-01-22
> **oldfred said:**
> If you erased entire drive what do you want to recover. 
With encryption, the entire idea is that data is not recoverable. You have to restore from backups.
But if you have old partition/volumes and passphrase it may be mountable and data recovered.
But I did not delete it, only the path was erased.

[IMG]https://i.imgur.com/Bc8qLbd.jpg[/IMG]

[IMG]https://imgur.com/Bc8qLbd[/IMG]
[IMG]https://imgur.com/Bc8qLbd[/IMG]
I do not need anything from the old system there,
Except for one thing, I have a password reserved for an external SD that I used to work on.
I encrypted the SD and set a password and forgot it.
And in the other system the password is reserved there, I just want to get my works out of the SD.
The system does not interest me.

---

### Post by oldfred on 2018-01-22
Please attach screenshots, not everyone has high speed Internet.
Easy to attach with forum's advanced editor and paperclip icon.

If you do not know password, there is no way to get to data.

       To get Ubuntu to see different encrypted install:
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sdb3 my-crypt
sudo os-prober
sudo update-grub

---

### Post by lionel4anlominus on 2018-01-23
> **oldfred said:**
> Please attach screenshots, not everyone has high speed Internet.
Easy to attach with forum's advanced editor and paperclip icon.

If you do not know password, there is no way to get to data.

       To get Ubuntu to see different encrypted install:
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sdb3 my-crypt
sudo os-prober
sudo update-grub


I know the password, I'll lose track to the disk.
I do not know how to recreate the path.
Through the new system I installed I can not get to the data as you said, because the drive is encrypted and the home folder.
I'd be happy if you could help me re-create a path.

---

### Post by oldfred on 2018-01-23
I do not know nor have ever used LVM, so not familar with its normal configuration. And yours looks like a custom configuration?

       Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995)

Someone posted this:

 sudo pvs
sudo vgs
sudo lvs
ls -l /dev/mapper
 df -hT | grep sd 

The first part is about mounting, so you can follow its instructions up to where it says you can do other tasks.

 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

---

### Post by lionel4anlominus on 2018-01-25
> **oldfred said:**
> I do not know nor have ever used LVM, so not familar with its normal configuration. And yours looks like a custom configuration?

       Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995)

Someone posted this:

 sudo pvs
sudo vgs
sudo lvs
ls -l /dev/mapper
 df -hT | grep sd 

The first part is about mounting, so you can follow its instructions up to where it says you can do other tasks.

 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

Thanks a lot this also taught me some new commands, but it did not really solve my problem.


Because my problem was, to create a new path to my old disk.

I do not know what details I need to add to my new GRUB.

---

### Post by TheFu on 2018-02-02
I use LUKS encrypted stuff all the time.
You don't need to tell grub anything to access files on the old disk.  You need to just mount the LV.  To do that, you need to 
* discover the encrypted partition
* use cryptsetup to unlock it (you must know the password, without that, forgetaboutit); there are no backdoors.
* use LVM tools to see the VG and LVs (sudo vgscan)
* mount each desired LV like it is a partition.  The paths are in /dev/mapper/ .... 
If the new system and old system use the same VG or LV names, there will be a clash and you'll need to rename the VG before it can be accessed.

After you access the data you want, make a backup, even if temporary, then format the disk and start over with or without encryption and/or LVM, as you desire.

If you are seeking to have the system mount the encrypted LVs automatically, after booting, then the fstab is where that happens.  There is a crypttab to prompt for the passphrase and unlock the encrypted partition.

No grub anything involved.

Or am i missing the question?

---

