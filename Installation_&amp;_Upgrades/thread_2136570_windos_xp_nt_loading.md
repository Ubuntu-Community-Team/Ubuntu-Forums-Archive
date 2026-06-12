---
title: "windos xp nt loading"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by Anoop Jose on 2013-04-18
hi,
i was running ma system with windows xp and i installed ubuntu 12.04lts also. after installation m unable to load xp. it doesnt ask which os to be loaded. it directly loads ubuntu. pls help

---

### Post by lisati on 2013-04-18
When you boot or restart your computer, hold down the left shift key. You *should* then see a menu offering a choice of which OS to start.

---

### Post by Anoop Jose on 2013-04-18
i tried the same but no response. ubuntu is loading as before

---

### Post by AnaheimSam on 2013-04-18
Hate to tell you this Anoop Jose, but you probably got rid of Windows when you installed Ubuntu.
It happened when I first installed Ubuntu.

You need to find out if you really did get rid of Win when you installed Ubuntu, so go to Disks. (Ubuntu logo>Type in "Disks">Press "Disks") and click on your hard drive. If you do not see any kind of NFTS partition or partition labeled as such, you know that you got rid of Windows.

---

### Post by Mark Phelps on 2013-04-18
When you installed Ubuntu, it overwrote the MBR to replace the Windows code with Linux code -- so now, it boots directly into Ubuntu.

When in Ubuntu, open a terminal and enter "sudo update-grub" -- and see if it finds Windows.

When done, reboot and see if you then get an OS selection menu.

---

### Post by Anoop Jose on 2013-04-18
this is wat i get

arun@arun-desktop:~$ sudo update-grub
[sudo] password for arun: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
arun@arun-desktop:~$

---

### Post by darkod on 2013-04-18
From ubuntu, open terminal and post the output of:
```
sudo parted -l
```

Lets see what partitions you have first of all. You should have ntfs partition for XP there. Maybe just the boot files are missing, especially if you had them on another partition separated from your XP partition. Windows can do this without even telling you, so later when you delete some partition you are in for a surprise.

---

### Post by Mark Phelps on 2013-04-18
> **Anoop Jose said:**
> this is wat i get

arun@arun-desktop:~$ sudo update-grub
[sudo] password for arun: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
arun@arun-desktop:~$

Not good ... no indication of Windows boot files found.  

Go with darkod's suggestion -- I'm afraid you may have replaced XP when you installed Ubuntu.

---

### Post by Anoop Jose on 2013-04-18
here 

arun@arun-desktop:~$ sudo parted -l
[sudo] password for arun: 
Model: ATA Hitachi HDP72502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  4000MB  4000MB  primary   linux-swap(v1)  boot
 2      4000MB  250GB   246GB   extended                  lba
10      4000MB  26.2GB  22.2GB  logical   fat32
 5      26.2GB  73.4GB  47.2GB  logical   ntfs
 6      73.4GB  105GB   31.5GB  logical   ntfs
 9      105GB   115GB   10.5GB  logical   ext4
 7      115GB   199GB   83.9GB  logical   ntfs
 8      199GB   250GB   50.8GB  logical   ntfs

---

### Post by darkod on 2013-04-18
That is not an automatic setup. You made it manually. The sda1 partition still has the boot flag but now it's linux swap partition. Do you remember whether it was ntfs before? I think your XP boot files were there. Windows needs as minimum the boot files to be on primary partition. All your other partitions are logical.

You have the size of the partitions there. Try opening your XP partition and browse if the data is thee. I think it should be.

When you open nautilus, on the left side under Devices you will have all these partitions listed. Clicking on one will open it so you can look around.

I assume you will only need to add the boot files but you can't do that on logical partition. And you have no unallocated space to make a new primary partition.

Why do you have so many different partitions? Unless you really need them I would suggest reorganizing the disk, with less partitions. Making too many partitions is not efficient because you have to have some free space on each, instead of using few partitions with combined size.

In any case, you could consider deleting sda1 and making primary ntfs partition in its place, but then you need to make a swap partition somewhere. Ubuntu can work without it, but depending on your RAM size and the tasks you use on the computer, you might need swap.

Bottom line, this has nothing to do with ubuntu, it seems you deleted the partition where the XP boot files were.

PS. Out of all those ntfs partitions, which one is the XP?

---

### Post by Anoop Jose on 2013-04-18
no.6 which is of 31.5 gb
and ubuntu no.9 10gb

---

### Post by darkod on 2013-04-18
sda6 is in the middle of the extended partition. If it was at the start or end, you could have converted it to primary. In this situation you can't.

What you decide to do, is up to you.

---

### Post by Anoop Jose on 2013-04-18
ok thanks darko

---

### Post by Anoop Jose on 2013-04-27
[FONT=arial black][/FONT]this is hw it looks now. hope this is good enough.

arun@arun-desktop:~$ sudo parted -l
[sudo] password for arun: 
Model: ATA Hitachi HDP72502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  31.5GB  31.5GB  primary   ntfs            boot
 2      31.5GB  250GB   219GB   extended                  lba
 5      31.5GB  47.2GB  15.7GB  logical   ext4
 6      47.2GB  51.4GB  4195MB  logical   linux-swap(v1)
 7      51.4GB  177GB   126GB   logical   ntfs
 8      177GB   250GB   72.8GB  logical   ntfs


arun@arun-desktop:~$

---

