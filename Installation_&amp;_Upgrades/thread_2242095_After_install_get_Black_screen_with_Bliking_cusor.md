---
title: "After install get Black screen with Bliking cusor"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by rickm1945 on 2014-08-30
I just installed Ubuntu 14.04.1 LTS on a Toshiba 1TB usb external HDD. At end of installation it tried to install /Boot on sda1 and failed. Then gave me a choice and I chose the Toshiba HDD. On restart all  got was a Black Screen with a blinking cursor at the top left side. I am having a heck of a time with this. I have and am using Ubuntu 14.04 LTS on a 160 GB external usb HDD and i has been awesome. Where should Grub2 be installed?

---

### Post by Bashing-om on 2014-08-30
rickm1945; Hi !

You install grub onto the hard drive ( external device ) that you have installed 'buntu onto in accordance with what you have set in bios as that primary booting device.

Look to know what the system recognizes the drives as:
```

sudo fdisk -lu

```
If this is a GPT partitioned device(s), then a different ball of wax, and will require a different tool to look.
If your motherboard is UEFI, then a whole different ball game.

The output of 'fdisk' will point to where/what to do .

[INDENT][INDENT][INDENT]it is a process
[/INDENT][/INDENT][/INDENT]

---

### Post by rickm1945 on 2014-08-31
Output of fdisk:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xeea60b3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000572ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1920159743   960078848   83  Linux
/dev/sdb2      1920161790  1953523711    16680961    5  Extended
/dev/sdb5      1920161792  1953523711    16680960   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

I installed Ubuntu 14.04.1 once using "Something Else." I wanted to have /boot, / (root)  /home and Swap but I still couldn't get it to boot. I have UEFI set to boot usb first. I have Ubuntu on a Toshiba usb 160 GB drive which runs flawlessly. I got the Toshiba 1TB drive Saturday to give Ubuntu lots of room. I intend to use Linux as my primary OS. I hate Windows 8.1.

---

### Post by rickm1945 on 2014-08-31
```

richard@richard-Studio-XPS-8100:~$ sudo parted -l
[sudo] password for richard: 
Model: ATA WDC WD10EZEX-22B (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  840MB   839MB   ntfs         Basic data partition          hidden, diag
 2      840MB   1113MB  273MB   fat32        EFI system partition          boot
 3      1113MB  1247MB  134MB                Microsoft reserved partition  msftres
 4      1247MB  162GB   161GB   ntfs         Basic data partition          msftdata
 5      162GB   983GB   821GB   ntfs         Basic data partition          msftdata
 6      983GB   1000GB  16.7GB  ntfs         Basic data partition          hidden, diag


Model: TOSHIBA MK1652GSX (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  152GB  152GB   primary   ext4            boot
 2      152GB   160GB  8512MB  extended
 5      152GB   160GB  8512MB  logical   linux-swap(v1)


Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdg: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  983GB   983GB   primary   ext4
 2      983GB   1000GB  17.1GB  extended
 5      983GB   1000GB  17.1GB  logical   linux-swap(v1)


richard@richard-Studio-XPS-8100:~$ 


```

This shows both usb HDD and Windows C: drive hope this might help.

---

### Post by rickm1945 on 2014-08-31
Thanks @Basing-om for your help and information. I have successfully installed and am running Ubuntu 14.04.1 LTS. I had to change UEFI to boot in EFI mode. I put live DVD in and booted up and reinstalled using "Something Else," went like a charm and I now have my Ubuntu on a 1TB Toshiba External HDD. The link you provided in your response gave me the answer to my problem. I will mark this thread as solved.Thanks again for the help it is much appreciated. Have a wonderful Labor Day!!:)

---

### Post by Bashing-om on 2014-08-31
rickm1945; Outstanding !

You do good work, pleased you have it all sorted out.

[INDENT][INDENT]now ain't ubuntu
[INDENT][INDENT][INDENT][INDENT]wonderful
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

