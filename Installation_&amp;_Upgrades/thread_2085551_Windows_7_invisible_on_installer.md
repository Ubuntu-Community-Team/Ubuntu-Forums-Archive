---
title: "Windows 7 invisible on installer"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by seshdroid on 2012-11-18
I decided to upgrade my system to a 64-bit Windows the other day alongside Ubuntu 12.04 and so I backed up all my data and formatted the entire disk and Installed Win-7 64-bit and created a 120 GB partition for Ubuntu (in Windows).

 Afterwards, when I wanted to install Ubuntu 12.04 32-bit, the installer failed to recognize the installed win-7 nor was I able to see the partition that I had created under 'Something Else'.

 I have read quiet a bit about it in various forums but none of it was giving me a proper solution. Each time I am getting one error on top of another.

 I've even tried entering various commands in the live-cd version but they don't seem to help installer recognize the Hard-Disk partition or installed windows7 

 I wanted to try WUBI but that only allows a max of 30 GB for Ubuntu (Kindly correct me if I am wrong)

Please help.

---

### Post by NikTh on 2012-11-18
Hi , 
this is probably a problem due to GPT table. Can you confirm that you have GPT and not MBR ? 

Boot from a LiveCD/DVD/USB of Ubuntu and open a terminal (CTRL+ALT+T) and give this command
```
sudo fdisk -l
``` 
Post the results back here. 

Also , are you sure that Windows was  shutdown properly  ? I mean , is not in hibernate mode or something like this.

---

### Post by darkod on 2012-11-18
On another note, why would you create a partition for ubuntu in windows since it can only create ntfs partitions and linux doesn't install on ntfs? You need to delete that partition and leave the space as unallocated.

Then you should be able to use it.

You better post the fdisk results as mentioned since it seems you have another issue too, not just the partition being ntfs.

---

### Post by oldfred on 2012-11-18
+1 on NikTh questions.

But why the 32bit version of Ubuntu. If system can run the 64bit Windows you probably should be running the 64bit version of Ubuntu. Also if partitioning is gpt then Windows is booting in UEFI mode and only the Ubuntu 64 version works with UEFI.

---

### Post by seshdroid on 2012-11-19
> **NikTh said:**
> Hi , 
this is probably a problem due to GPT table. Can you confirm that you have GPT and not MBR ? 

Boot from a LiveCD/DVD/USB of Ubuntu and open a terminal (CTRL+ALT+T) and give this command
```
sudo fdisk -l
```Post the results back here. 

Dear NikTh, Thank you so much for the quick reply, I'm posting the result of sudo fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ed01aef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   379379711   189586432    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c944

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15633407     7816688    b  W95 FAT32
ubuntu@ubuntu:~$ 

```> Also , are you sure that Windows was  shutdown properly  ? I mean  , is not in hibernate mode or something like this.Yes, I did make sure that the windows was shutdown properly before i rebooted the computer to install Ubuntu.
I'm sorry for the late reply. It was night for me here.

---

### Post by seshdroid on 2012-11-19
> **oldfred said:**
> +1 on NikTh questions.

But why the 32bit version of Ubuntu. If system can run the 64bit Windows you probably should be running the 64bit version of Ubuntu. Also if partitioning is gpt then Windows is booting in UEFI mode and only the Ubuntu 64 version works with UEFI.


 Hi oldfred,

 Thank you for your reply. Yes, it seems stupid to use the 32-bit 12.04 but the results at the installer are the same. Moreover in the 64-bit, there are serious WiFi driver issues. I use a lenovo x120e which accepts the default drivers that comes out of the box with the 32-bit 12.04 but for some weird reason does not work at all with the 64-bit one. Now I've tried all sorts of drivers default, proprietary, old and new but they show the same result. No stable connection. 

Wi-fi works well on the 64-bit 12.10 but again  I have the installer issue. 

I've given up on that one but I'm not giving up on this issue.

---

### Post by seshdroid on 2012-11-19
> **darkod said:**
> On another note, why would you create a partition for ubuntu in windows since it can only create ntfs partitions and linux doesn't install on ntfs? You need to delete that partition and leave the space as unallocated.

Then you should be able to use it.

You better post the fdisk results as mentioned since it seems you have another issue too, not just the partition being ntfs.

Hi Darkod, 

 Thanks for your reply. Initially, I did not bother with the partition, I just installed windows 7 and shut it down and rebooted the system with the usb-stick to install Ubuntu. I saw that the installer did not recognize windows. 

 I then thought, perhaps by splitting the disk I might be able to figure out a partition where I can install Ubuntu. So I went back to windows and created an unallocated 120GB partition to install it. The Installer still did not recognize the partition. Shows it as a full disk.

---

### Post by darkod on 2012-11-19
Look at the warning about GPT in the fdisk results. It says the disk /dev/sda has gpt table. But the partitions listed on /dev7sda look like msdos partitions.

This situation happens if the disk was with gpt table earlier, and you used windows to write a new msdos table. Windows doesn't delete the backup gpt table which linux can see and gets confused what is what.

Use fixparts (you can do it from ubuntu live session) and it will offer to remove the gpt table remains. Just confirm and after that all should be fine.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Just open the disk with fixparts like:
sudo fixparts /dev/sda

and it will offer to do it for you. You have to install it first though, you have the instructions on their website.

---

### Post by seshdroid on 2012-11-19
Cheers Darkod, I'll get back with the results pretty soon :)

---

### Post by seshdroid on 2012-11-19
> **darkod said:**
> Look at the warning about GPT in the fdisk results. It says the disk /dev/sda has gpt table. But the partitions listed on /dev7sda look like msdos partitions.

This situation happens if the disk was with gpt table earlier, and you used windows to write a new msdos table. Windows doesn't delete the backup gpt table which linux can see and gets confused what is what.

Use fixparts (you can do it from ubuntu live session) and it will offer to remove the gpt table remains. Just confirm and after that all should be fine.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Just open the disk with fixparts like:
sudo fixparts /dev/sda

and it will offer to do it for you. You have to install it first though, you have the instructions on their website.

SOLVED!!! Thanks a lot Darkod, you're a star :)
I did everything as you had advised me
i.e  I installed fixparts by downloading the deb package from their website, I  typed in **sudo fixparts /dev/sda **
it told me that there are certain things that needed to be done, pressed **Y**
saved changes with [B]w
[/B]and that was it.  
I did another **sudo fdisk -l  **and this time I saw no errors
I ran the install and everything went as smooth as silk 

You know, Living without Ubuntu drives me into some sort of depression. I've been with it for about 3 years now and each day I learn something new and exiting. I've not tinkered around it ( OS) a lot, Mostly I use Chromium, QGIS, GRASS and Python. My Uni forces me to use Windows and ArcGIS which is a real pain in the back-side.  Hopefully one day I don't have to install windows or any other proprietary software at all.

---

### Post by darkod on 2012-11-19
Glad you got it going. Actually I can't take all the credit, if you see Nik mentioned right away in his first post that usually gpt remains can do this.

It was a joint effort. :) Enjoy it now.

---

