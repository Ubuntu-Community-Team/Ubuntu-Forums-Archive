---
title: "how do i reinstall ubuntu from 32bit to 64bit?"
date: 2016-11-11
forum: Installation &amp; Upgrades
---

### Post by rophi on 2016-11-11
_**[SIZE=3]How I got into this mess[/SIZE]**_ 
     I'm a new ubuntu convert and tried dual booting my lenovo ideapad 100  with Ubuntu gnome and windows 10. Turns out i failed, I installed ubuntu  in legacy mode because that was the only way the laptop would let me. I  didn't delete my windows partitions but windows 10 can't boot now, I  guess I will need to reinstall it in legacy mode (How do I do that?  Being able to use my old partitions would be great too).
_**[SIZE=3]What I need[/SIZE]**_
     Another  problem I have is that I installed the ubuntu GNOME 32 bit version,  thinking I couldn't use the 64 bit version called AMD64, because i have  an intel processor( Only later did I realize that i can, and should've  installed that). So I looked around and found that I can somehow upgrade  it in the terminal, but that reinstalling it completely is better and  less hassle. This being an almost clean install I don't mind  reinstalling, but how am I supposed to do that? ( + I've already flashed  the needed 64 bit image on a USB)
[U][B][SIZE=3]Additional info
[/SIZE][/B][/U][SIZE=3][SIZE=1][SIZE=2]     Here's my boot info if that helps. [http://paste2.org/A0ZX9f7m](http://paste2.org/A0ZX9f7m)[/SIZE][/SIZE][/SIZE][U][B][SIZE=3]
[/SIZE][/B][/U]**[SIZE=3][SIZE=1][SIZE=2][/SIZE][/SIZE][/SIZE]**[SIZE=3][SIZE=1][SIZE=2][/SIZE][/SIZE][/SIZE]

---

### Post by oldfred on 2016-11-12
Another thread on that model:
LENOVO Ideapad 100 Laptop 16.04 Dual Boot  
[https://ubuntuforums.org/showthread.php?t=2336544](https://ubuntuforums.org/showthread.php?t=2336544) 

If you are reinstalling only use the Something Else install option and choose existing / (root) as new / partition.

Can you boot Windows directly from UEFI boot menu. Grub in BIOS mode cannot boot Windows in UEFI mode.
And if Windows hibernation or fast startup is on, you can only boot it from UEFI.

      How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)

---

### Post by rophi on 2016-11-12
My problem is that I can't get into windows, I failed dual booting and now I'm left with a 32 bit ubuntu gnome which I want to upgrade to 64 bit ( I was confused when choosung AMD64, since I have a intel processor). How do I either fix my windows problem so I can then boot in windows and fix this or how can I install a 64 bit Ubuntu OS on a 32 bit Ubuntu OS? People on askUbuntu ([http://askubuntu.com/questions/848397/how-do-i-reinstall-ubuntu-from-32-bit-to-64-bit](http://askubuntu.com/questions/848397/how-do-i-reinstall-ubuntu-from-32-bit-to-64-bit)) tell me that I should fix my windows problem first and then fix my ubuntu problem but I don't even know how to do that

---

### Post by oldfred on 2016-11-12
Can you boot Windows directly from UEFI boot menu?
Can you still boot Ubuntu installer, either the 32bit or 64 bit in either boot mode?
You just about have to use your Windows repair/recovery disk to fix most Windows issues. You did make one?
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

From Linux you can only do very minor repairs of Windows.

If you can boot any Ubuntu post this from terminal:
sudo parted -l

For UEFI boot please review link in my signature. It is a lot and has a lot of useful links to even more info.
Some you can skip, but you need to at least review install instructions.

---

### Post by rophi on 2016-11-12
I can only boot  in Ubuntu GNOME 32 bit, windows 10 doesn't load( Probably because i failed and installed ubuntu on legacy mode, while windows 10 is in UEFI). I don't have a windows repair disk but I will try making one in the morning. Here's some pictures of how everything looks for me [IMG]file:///home/boi/Downloads/20161113_004122.jpg[/IMG] [IMG]file:///home/boi/Downloads/20161113_004050.jpg[/IMG] . And here's what my terminal gave me:

```
sudo parted -l
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  274MB   273MB   fat32        EFI system partition          boot, esp
 2      274MB   290MB   16,8MB               Microsoft reserved partition  msftres
 3      290MB   638GB   638GB   ntfs         Basic data partition          msftdata
 8      638GB   738GB   100GB   ext4
 9      738GB   953GB   215GB   ext4
10      953GB   953GB   13,6MB                                             bios_grub
 4      953GB   980GB   26,8GB  ntfs         Basic data partition          msftdata
 5      980GB   981GB   1049MB  ntfs         Basic data partition          hidden, diag
 6      981GB   999GB   18,5GB  ntfs         Basic data partition          diag
 7      999GB   1000GB  1049MB  fat32        Basic data partition          hidden, msftdata




```

---

### Post by oldfred on 2016-11-13
You should be able to directly boot Windows from Windows entry in UEFI. You may have to turn on UEFI boot or turn off BIOS/CSM/Legacy boot settings.
Some auto switch based on which mode the entry is for. 
You cannot boot Windows in UEFI mode from grub menu in BIOS mode. You cannot switch boot modes once you start booting.

---

