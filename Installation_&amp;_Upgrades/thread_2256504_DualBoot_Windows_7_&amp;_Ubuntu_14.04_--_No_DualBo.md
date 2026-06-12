---
title: "DualBoot Windows 7 &amp; Ubuntu 14.04 -- No DualBoot Screen"
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by SternH on 2014-12-13
Hi,

I'm new to using Ubuntu, and I've recently install Ubuntu on my Windows 7 with the following steps:

1. shrink harddrive by 100GB
2. make bootable USB using UUI
3. Boot into USB, ran installation "Install alongside Windows 7".
4. Reboot

Now my computer automatically boots into my Ubuntu partition without showing a Boot menu.

I've tried using Boot Repair, to no avail. 

When I search for the same problem, it seems most people are getting the opposite. That is, they can only boot into Windows. 
I'm not really sure what to do now.

I'm going to try booting into a windows USB and running boot repair, and hope that fixes it. Since it might not work, any suggestions would be greatly appreciated.

Thanks in advance.

---

### Post by carl4926 on 2014-12-13
Open a terminal and get us the result of

```
sudo parted -l
```

Also what is the feedback from 

```
sudo update-grub
```

---

### Post by SternH on 2014-12-13
```
stern@SternDesktop-PC:~$ sudo parted -l
Model: ATA WDC WD10EADS-11M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   893GB   893GB   primary   ntfs
 3      893GB   1000GB  107GB   extended                  lba
 5      893GB   992GB   98.9GB  logical   ext4
 6      992GB   1000GB  8439MB  logical   linux-swap(v1)


Model:   (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  16.0GB  16.0GB  primary  ntfs


```

```
stern@SternDesktop-PC:~$ sudo update-grub
[sudo] password for stern: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sdb1
done

```

---

### Post by SternH on 2014-12-13
If i'm not wrong, partition 1 and 2 is my windows. I'm not sure what 3 is, 5 would be my root directory for ubuntu, and 6 is swap.

Thanks

---

### Post by fantab on 2014-12-13
```

stern@SternDesktop-PC:~$ sudo parted -l
Model: ATA WDC WD10EADS-11M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   893GB   893GB   primary   ntfs
 3      893GB   1000GB  107GB   extended                  lba
 5      893GB   992GB   98.9GB  logical   ext4
 6      992GB   1000GB  8439MB  logical   linux-swap(v1)
```

The 3rd partition or /dev/sda3, is the Extended partiton. The 'msdos' partition table has only 4 Primary Partitions limit. Extended partition removes the limitation by acting as a single partition which contains further Logical partitions (more than 100). So your 4th and 5th partitions are Logical Partitions within the 3rd Extended partition.

The 'msdos' partition table [MBR] is being replaced with newer and advanced GUID Partition table [GPT].

> I've tried using Boot Repair, to no avail. 


Boot Repair would have asked you to note down the url to the bootinfo file, can you post the url here?
If not, run Boot Repair again and run 'create bootinfo summary' option, note down the url to the file and post it here.

---

### Post by carl4926 on 2014-12-13
This is a little odd
```
[COLOR=#000000][FONT=Ubuntu Mono]Found Windows 7 (loader) on /dev/sda1
[/FONT][/COLOR]Found Windows 7 (loader) on /dev/sda2 
[COLOR=#000000][FONT=Ubuntu Mono]Found Windows Recovery Environment (loader) on /dev/sdb1[/FONT][/COLOR]
```

---

### Post by carl4926 on 2014-12-13
sda1 looks like it might be the windows boot partition, it has the boot flag on it, but you never know.
But I'd examine the content on both to see which has bootmgr or even if it exists on both

---

### Post by oldfred on 2014-12-13
If you ran Boot-Repair it copied bootmgr & BCD to main install. Too many users did not know what a boot partition is and just delete it and then wonder why they cannot boot.
But then grub2's os-prober finds boot files in boot boot partition and main install and either should work to boot. Boot partition should also have repair console so f8 may work. Not sure if then booting sda2 and using f8 would work at all. And usually grub booting Windows does not give enough time to for f8 to be seen by Windows.

It looks like you should have Windows in grub menu. If menu is not appearing hold shift key from BIOS until menu appears.

---

### Post by SternH on 2014-12-13
Here's what I got from running boot-repair:
[http://paste.ubuntu.com/9498678/](http://paste.ubuntu.com/9498678/)

Sorry I didn't post this update earlier, but here's what I've tried:
FixParts: didn't do anything
Windows Startup Recovery: found no errors (looks like it looks at the last windows bootup record)
grub-customizer: I moved sda1 to the top, and now I boot straight into Windows

I'll remake my ubuntu USB and run boot repair from there. That's supposed to fix it, but if it doesn't I'll post here.

---

### Post by carl4926 on 2014-12-13
Have you tried as suggested
> [COLOR=#000000]If menu is not appearing hold shift key from BIOS until menu appears[/COLOR]

---

