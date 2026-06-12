---
title: "Bootable for camera and backup for Windows"
date: 2022-07-14
forum: Installation &amp; Upgrades
---

### Post by dynvec on 2022-07-14
I just got an SD card for a camera with the Amazon seller being the manufacturer (as one may see on [SanDisk 256GB Extreme MicroSDXC UHS-I Memory Card - C10, U3, V30, 4K, A2, Micro SD - SDSQXA1-256G-GN6MN : Amazon.ca: Electronics]("https://www.amazon.ca/gp/product/B082WNC4NK/")) so I doubt I got a counterfeit (which are numerous on Amazon). The card is specifically for a camera, which I'm convinced use exFat even though I haven't received it yet; I'd like to also use it as a bootable Ubuntu device as well as backup storage for my desktop (running Windows 10). I was hoping I could choose the file system for the bootable Ubuntu but I wasn't asked when using the software recommended by the installation tutorial, that is balenaEtcher as may be seen on [Install Ubuntu desktop | Ubuntu]("https://ubuntu.com/tutorials/install-ubuntu-desktop").

In the verification process of the bootable Ubuntu creation process, it failed as well as had my windows disconnect the device and create multiple drives. At first it was only 1 extra drive (2 total), but then I thought there was a bug with Windows so I rebooted, then there was 2 extra drives. Although I like to have a backup OS in case my main fail, a large reason I want a bootable Ubuntu is for my laptop, which already had the previous LTS version; so I booted with my laptop and it recognized the SD card. I then restarted the laptop using the SD card to boot and it failed to do so, I then did a plain restart (booting with the previous LTS) and loaded its disk utility.

It turns out the 256 GB SD card has for partition, in order
[LIST=1]
[*]3.7 GB of ISO 9660 
[*]4.3 MB of FAT 
[*]307 KB of Basic Data (what's that?) 
[*]252 GB of Ext4 
[/LIST]

Thank you kindly for your help

**Update 1**

The version I put on the SD card that both failed to verify on my Windows desktop and live boot on my laptop was ubuntu-22.04-desktop-amd64.iso, which was successfully chesksumed. None of the partition from the SD card after the verification failed could be accessed by Windows, it asked if I wanted to format them.

---

### Post by yancek on 2022-07-15
When trying to boot the 'live' Ubuntu 22.04 on the SD Card, did you set it to first boot priority in the BIOS firmware?  Are your installed windows and Ubuntu systems both UEFI?  Did you or can you boot the SD Card from the UEFI boot menu in the BIOS?  Windows shoold have at least recognized the 2 windows partitions and I don't know what they are.  Windows will not recognize the ext4 partition on the Card which is by far the largest partition.

---

### Post by dynvec on 2022-07-15
> **yancek said:**
> did you set it to first boot priority in the BIOS firmware?  Are your installed windows and Ubuntu systems both UEFI?  Did you or can you boot the SD Card from the UEFI boot menu in the BIOS?
I changed my BIOS settings enabling UEFI, the boot drives were only in order DVD & SSD. I rebooted using the BIOS key and there's an initial menu which the last option lead to a regular BIOS menu, before that includes the drives, that selecting them will attempt to boot from; earlier the drive list there was DVD, SSD & SD card, after the BIOS change an option was appended UEFI: SD card, which I selected. Almost immediatly after there was a black screen with only line: error reading /boot/. Soon after the Ubuntu booting menu displayed and I selected Try or install Ubuntu (the 2nd option was safe mode and a few options more).

Then there was an alternate that switched every ~2 mins from a black screen with a fixed vertical bar to a plain black screen for > 5 mins (I think almost 10). Then there was a black screen with
> error: failure reading sector 0x0 from hd0
error: you need to load the kernel first.

Press any key to continue...
for < 1 min then the Ubuntu booting menu returned (starting with Try or install Ubuntu). I tried this 3 times with very similar result.

I'd rather not reboot Windows 10 unless I have to considering with the amount of software I usually have on, that fully loading as I want to takes almost 10 mins. I went into Start > Windows Administrative Tools > System Information then once that was loaded I left it at the default System Summary and in the table, the BIOS Mode value was UEFI.

**Update 1**

I saw that Ubuntu 22.04.1 will be released in ~3 weeks but I need to setup my SD card ASAP for my camera. Is there a way to set its partitions so when it's released it won't touch the partition for the camera (secondary use to back up Windows) ? Perhaps set the 1st 10 GB to ext4 then the remainder exFat, so later the ext4 can be broken into whatever Ubuntu would like? Upgrading the laptop OS isn't a priority, so the ~3 weeks wait is no issue, and I have a live version of the previous LTS in case my Windows breaks.

---

### Post by tea for one on 2022-07-16
Have you checked if your camera will accept an SD Card with multiple partitions (inc ext4)?

---

### Post by sudodus on 2022-07-16
> **tea for one said:**
> Have you checked if your camera will accept an SD Card with multiple partitions (inc ext4)?
+1

I would suggest that you dedicate an SD card to your camera (this one or another one, if you think this one is too big for the camera).

So you should have separate drives,

- an SD card for the camera
- an SD card, a USB pendrive or (fastest and most reliable) an SSD connected via USB 3 for a portable external operating system for the computers.
- an external HDD (or SSD) for backup. SD cards or USB pendrives are not reliable enough for backup.

There are several reasons:

- SD cards have a limited life-time, they wear quickly due to repeated write operations. This is not a problem in a camera, but when you use it as system drive for an operating system, there will be a lot of write operations onto the same memory locations (much more than when only storing pictures or video clips). And you would not want your card to suddenly lose all saved {pictures/video clips}.

- It might be difficult to make both the camera happy for the card as storage and the computer happy for the card as system drive of an operating system. Usually it is best to let the camera format the card.

---

### Post by dynvec on 2022-07-16
> **tea for one said:**
> Have you checked if your camera will accept an SD Card with multiple partitions (inc ext4)?
> **sudodus said:**
> +1
I have not received it, it's nearby but in a governmental facility, so unreachable until it gets here; but in the meanwhile I need to use it in a backup device to take pictures (cell phone without SIM).

> **sudodus said:**
> they wear quickly due to repeated  write operations. [...] there will be a lot of write  operations onto the same memory locations
I have 0 intention of including a partition to make the live Ubuntu keep its session, that is it will "forget" everything when the system is powered up, just like years ago it would be when booting from a finalized CD (unable to write anything on it anymore).

> **sudodus said:**
> It might be difficult to make both the camera happy for the card as  storage and the computer happy for the card as system drive of an  operating system.
I'm asking here in case someone has, or know how to, make it happen, so I can do it in advance. As mentioned in my previous update (of my previous post), I don't intend on putting Ubuntu right away on the SD card anymore, just prepare it so it can be done when Ubuntu 22.04.1 is released.

**Update 1:** Fixed typo.

---

### Post by sudodus on 2022-07-16
I know many ways to make a live Ubuntu system on a card, pendrive, SSD, HDD, DVD disk. And I have an experience of cameras that may have problems with a card unless there is one single partition with FAT32 or exFAT. I have no new camera, so my experience may be a little old there.

It is rather quick and easy to try what works and what does not work, but difficult to guess. So I suggest that you wait until you have the camera. Then you can use some different methods.

- First let the camera format the card and check that it works.

- Put the card in the computer and check the partition table and file system with for example with
```

fdisk -lu

```
- After that you know what the camera prefers. It might work with some other partition table and/or file system too.

If you want more help, post the output of the [FONT=Courier New]**fdisk**[/FONT] command, and we can suggest what kind of method is likely to work in order to create a live Ubuntu system.

Windows may stop seeing the file system if you let Ubuntu modify the size. The same might happen with the camera, so you had better create the correct partition table and file system at once.

If I must guess now, I suggest that you try [Oldfred's classic extraction method](https://help.ubuntu.com/community/Installation/iso2usb#For_an_UEFI_only_boot_flash_drive_you_need_no_installer), which is a very simple way to make a bootable Ubuntu drive for UEFI mode (works except in very old computers).

- The simple method to make one single big partition is probably most likely to work. You would mix pictures and video clips with Ubuntu system files, but I think you can stand that.

- The next step would be to try with different partitions for the camera (let it use the first partition) and for Ubuntu (let it use the second partition).

---

### Post by tea for one on 2022-07-17
> **sudodus said:**
> 
So you should have separate drives,

- an SD card for the camera
- an SD card, a USB pendrive or (fastest and most reliable) an SSD connected via USB 3 for a portable external operating system for the computers.
- an external HDD (or SSD) for backup. SD cards or USB pendrives are not reliable enough for backup.

Yes, complete agreement with sudodus. This is exactly the correct procedure.

Anyway, I was curious about the idea of a multi-use SD card, so I had a little play with the concept.

In essence, it is possible to do what you want (assuming your hardware is compliant).
My digital camera is approx 8 years old and will only find the first partition on the SD Card.
Consequently, I had to extract the Ubuntu 22.04 iso (using oldfred&#8217;s classic extraction method) to the second partition.
The third partition was deliberately created as ntfs for Windows 11.
Therefore, I ended up using a msdos partition table and 3 partitions as follows:-

```
ubuntu@ubuntu:~$ lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint,parttypename
NAME          SIZE TYPE FSTYPE FSUSE% FSAVAIL MOUNTPOINT                                         PARTTYPENAME
mmcblk0      29.5G disk                                                                          
&#9500;&#9472;mmcblk0p1    10G part vfat       5%    9.4G /media/ubuntu/A0B7-75DE                            W95 FAT32
&#9500;&#9472;mmcblk0p2     5G part vfat      68%    1.6G /cdrom                                             W95 FAT32
&#9492;&#9472;mmcblk0p3  14.5G part ntfs       8%   13.3G /media/ubuntu/1928980C1955A308                     HPFS/NTFS/exFAT
ubuntu@ubuntu:~$

```
The iso boots (in UEFI mode) and the code block above is from the live session.
My camera can use the first partition and Window files can be sent to the ntfs partition.

Three partitions may not be essential but it affords a degree of tidiness.
I also wanted to experiment with booting an iso not installed on the first partition.
My Motorola G7 (Android) will also read and write to the first partition.

Interesting exercise but, as mentioned by sudodus, I would also be concerned about backing up important data to an SD Card.

---

