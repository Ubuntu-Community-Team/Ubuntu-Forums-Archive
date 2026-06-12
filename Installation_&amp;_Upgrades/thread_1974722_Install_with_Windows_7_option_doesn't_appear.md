---
title: "Install with Windows 7 option doesn't appear"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by Gonza10 on 2012-05-06
Well i am a Windows user, and I want to try out Ubuntu for the first time the thing is that after i check download options and get third party downloads or something like that and press continue. The option Install with Windows 7 (dual-boot)option does not appear. The only two options that DO appear is:
 [LIST]
[*]Install Ubuntu(don't remember really what it says, i know it will erase my windows)
[*]Something else
[/LIST]. 

I don't want to erase my windows and i don't know anything of ubuntu partitions to click on the something else option. 

I had the same problem with ubuntu 11.10 and I downloaded 12.04 thinking that maybe the problem was solved but guess not. 

How do i get the Dual-boot option? 

I am running a 64 bit notebook.
Also im booting from a USB drive. 
Have one partition where the windows is installed.

---

### Post by darkod on 2012-05-06
Boot the cd first in live mode, Try Ubuntu. Open terminal and post the result of:
sudo fdisk -l (small L)

This can happen if there is an error or corruption in the partition table and it can't see win7. So the option is not there.
Or if the disk has been used in raid earlier and has meta data remains.
Or if it's a dynamic disk in windows because that is MS format.

---

### Post by Gonza10 on 2012-05-06
Is this it? 
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x135c058f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   600246271   299918336    7  HPFS/NTFS/exFAT
/dev/sda3       600248320   625139711    12445696    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4025 MB, 4025810432 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4ed44ed3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          38     7839719     3919841    b  W95 FAT32

---

### Post by darkod on 2012-05-06
It looks good. Do you know if the disk has been used in raid before? Since you are not running raid, it doesn't hurt trying to remove the meta data remains. Boot into live mode and in terminal:
sudo dmraid -E -r /dev/sda

If that asks you to remove raid data, confirm. After that try to install again.

Also, if you don't have unallocated (unpartitioned) space on the disk ready for ubuntu, you will need to shrink one of the partitions to make space. It's best to do it from windows Disk Management. Reboot windows few times after that. Then you can install ubuntu.

---

### Post by Gonza10 on 2012-05-06
I don't even know what raid is so I guess it has never been raid.

I tried removing the meta remains but it says no raid disk and with names: /dev/sda

I'll create a new partition for the ubuntu installation is 20gb good or will i need more? 

Also how can I acess the stuff I have on my windows partition from my Ubuntu, say I want to watch a movie thats in the windows partition what should i do? 

Thanks for everything

---

### Post by oldfred on 2012-05-06
DO NOT create partitions with Windows. Use Windows to shrink the NTFS partition to make space for Ubuntu, but if you use Windows to create partitions it may convert to dynamic partitions and not work with Linux.

You can use 20GB, normally you want another partition for swap and both partitions can be in an extended partition. All MBR(msdos) computers have a 4 primary partition limit, but one partition can be converted to an extended partition and hold many logical partitions. Linux will boot from logical partitions just fine.

Ubuntu has the NTFS driver so it can read & write to NTFS formated partitions, but Windows does not like too much writing into it, reading is ok. If wanting to write into a partition that Windows can use, it is better to create a shared NTFS formated data partition ( d: drive in Windows). It also can be a logical partition.

---

### Post by Gonza10 on 2012-05-06
I thought that by shrinking it to 20gb it would create a swap partition inside of it.

Sorry, I don't get what you are trying to say. 

Let me sketch out what i want. One partion to save the windowsOS, another to save all my documents programs readable/writeable for both OS. And last my ubuntuOS.

How can it be done?

---

### Post by darkod on 2012-05-06
20GB including swap is a little low. Try assigning it 20GB + swap size.

Swap can be as small as 2GB if you don't plan to hibernate ubuntu, but if you want to hibernate ubuntu it needs to be approx 1.5 x RAM size. So, it will depend on your ram size.

Shrink one of the partition for as much as you need, and don't worry about partitions right now. You are only using 3 primary partitions.

If you are installing ubuntu with the manual method (doesn't sound like it), create the root and swap partitions as logical.
If you install with the auto method, it will create them as logical anyway.

So, they will be two separate logical partitions, inside one extended partition. That makes it 3 primary + 1 extended, just inside the 4 partitions limit. Case closed. :)

Just shrink with windows Disk Management to make enough unpartitioned space, and DO NOT create any partitions from windows. Leave it as unpartitioned. The ubuntu installer will do its thing.

---

### Post by Gonza10 on 2012-05-06
Ok, thats makes 4gb ram x 1.5 = 6gb + 20gb for evreything else = 26gb. 

What about the one that I cant read/write from both OS? 

Sorry, i'm really new to this. Don't want to mess anything up.

---

### Post by darkod on 2012-05-06
oldfred was talking about the win7 system partition, partition C:. Ubuntu can read/write it because it's ntfs, but win7 can detect another OS was accessing it and sometimes it doesn't like it and can go mad. That's windows.

The other two ntfs partitions, you can do what ever you want. But because on C: there are windows system files, it can be problematic.

Of course, nothing is stopping you writing to that partition from ubuntu. Up to you. :)

But I am still concerned you were not given the option to install aside windows. If it can't see it from what ever reason, it will not include it in the boot menu so you will end up with a bootloader that boots directly ubuntu (thinking there is nothing else to boot).

Before starting all this, try running chkdsk on C: in windows. Sometimes ubuntu can detect some errors waiting chkdsk to be run, and ignores that partition. If it ignores it, it can't see win7 is on it. Try running from a command prompt Run As Administrator:
chkdsk c: /r /f

---

### Post by Gonza10 on 2012-05-06
This is what it says after i chkdsk:

The type of the file system is NTFS.
Cannot lock current drive.

Chkdsk cannot run because the volume is in use by another process.
Would you like to schedule this volume to be checked the next time the system restarts? (Y/N)

Remember I couldn't remove the meta remains. :


no raid disk and with names: /dev/sda

---

### Post by darkod on 2012-05-06
Well, if you feel up to it, say Yes and restart. It will start the check, and boot windows when it's done.

---

### Post by Gonza10 on 2012-05-06
Ok, after it checks it what should i do?

shrink the 26gb?

---

### Post by darkod on 2012-05-06
Yeap, and then again start the install with the ubuntu cd and see if the Install along win7 option is there. That would mean it can detect it.

If it doesn't detect it, it's up to you if you want to continue installing and use the Something Else (manual) option.

---

### Post by Gonza10 on 2012-05-06
Great, one last question i'm concerned about what you said that. Windows doesn't like ubuntu getting inside the system files.

So i should shrink twice the partion one for the ubuntuOS(10gb for the swap and ubuntufiles)
and the other one much bigger to save all my files music ,movies etc to be accessed by both OS? can it be done

---

### Post by oldfred on 2012-05-06
It can be done, the main issue is how much free space do you have? And how large is your data.

As always good backups for any system change is a good idea.

---

### Post by Gonza10 on 2012-05-06
Well I can pass all my data to my ExternalHD i think i will have about 160gb of free space or more.

---

