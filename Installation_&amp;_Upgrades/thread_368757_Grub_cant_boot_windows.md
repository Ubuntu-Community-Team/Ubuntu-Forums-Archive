---
title: "Grub cant boot windows"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by sephirothsigep on 2007-02-23
alright so i just installed ubuntu 6.10 on my first harddrive first partition. my 3 partition is linux swap . and then my 2 partition is a logical partition. partition 5 is then my windows xp partition. then partition 6 is a ntfs i have for beyond tv(would be using mythTV but tuner card does not work with mythTV) and then partition 7 is fat 32 so that i can manipulate file that i use on both.

[SIZE="3"]fdisk output[/SIZE]
```
sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1207     9695196   83  Linux
/dev/hda2            1306        4864    28587667+   f  W95 Ext'd (LBA)
/dev/hda3            1208        1305      787185   82  Linux swap / Solaris
/dev/hda5            1306        2219     7341673+   7  HPFS/NTFS
/dev/hda6            2220        4227    16129228+   7  HPFS/NTFS
/dev/hda7            4228        4864     5116671    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7475    60042906    7  HPFS/NTFS

Disk /dev/hdd: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        1216     9767488+  83  Linux
```

[SIZE="3"]Grub menu.lst[/SIZE]
```

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
anyway i just want to be able to get back to my windows side

---

### Post by Herman on 2007-02-23
Hello sephirothsigep,
What was in partition number 1 before you installed Ubuntu in it? 

Windows 'boot partition'?

---

### Post by thelocust on 2007-02-23
Try this:

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader	+1

---

### Post by sephirothsigep on 2007-02-23
> **Herman said:**
> Hello sephirothsigep,
What was in partition number 1 before you installed Ubuntu in it? 

Windows 'boot partition'?

i am assuming that yes that was where the "windows 'boot partition' " was.
when i installed xp i created that partition and just gave it a ntfs format that i then wrote over when i installed linux caused this problem. i then created a second partition that is my windows partition. and then left the rest of the drive unallocated. the reason that i did this is i wanted to put  linux at the beginning of the drive. dont ask me why i really dont know now that i think about it.

---

### Post by sephirothsigep on 2007-02-23
> **thelocust said:**
> Try this:

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader	+1

nope no luck gives me error 13. another thing my xp partition is not on hard drive 1 its on hard drive 0 on partition 5 so i dont see how mapping that change will make a difference

the partition is bold is my windows partition. 
the partition in RED is a logical partition

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1207     9695196   83  Linux
[COLOR="Red"]/dev/hda2            1306        4864    28587667+   f  W95 Ext'd (LBA)[/COLOR]
/dev/hda3            1208        1305      787185   82  Linux swap / Solaris
**/dev/hda5            1306        2219     7341673+   7  HPFS/NTFS**
/dev/hda6            2220        4227    16129228+   7  HPFS/NTFS
/dev/hda7            4228        4864     5116671    b  W95 FAT32

FOUND THIS information not sure if it will help or not 
>      (hd0,1)

Here, `hd' means it is a hard disk drive. The first integer `0' indicates the drive number, that is, the first hard disk, while the second integer, `1', indicates the partition number (or the pc slice number in the BSD terminology). Once again, please note that the partition numbers are counted from zero, not from one. This expression means the second partition of the first hard disk drive. In this case, GRUB uses one partition of the disk, instead of the whole disk.

     (hd0,4)

This specifies the first extended partition of the first hard disk drive. Note that the partition numbers for extended partitions are counted from `4', regardless of the actual number of primary partitions on your hard disk.

     (hd1,a)

This means the BSD `a' partition of the second hard disk. If you need to specify which pc slice number should be used, use something like this: `(hd1,0,a)'. If the pc slice number is omitted, GRUB searches for the first pc slice which has a BSD `a' partition. 

---

### Post by Herman on 2007-02-23
I hate to tell anyone bad news, but I don't believe it is possible to boot Windows in a logical partition without it having another Windows in a primary partition to boot through. :(

The Windows default method for booting more than one Windows install is (so I have read), to install the boot loader for the subsequent Windows system in the original Windows installation. When the original Windows installation gets a virus and needs to be re-installed, or is deleted and replaced with Linux, you lose both operating systems.
If you had known that earlier and you already had Linux installed, you could have used grub's hide and unhide commands to allow the second Windows installation to proceed in another primary partition independant from the earlier installation. [Super Grub Disk]("http://supergrub.forjamari.linex.org/") has features to make that even easier for beginners, or people without Grub installed to hard disk. Just remember that for next time ;)

Can you look inside your Ubuntu  hda5 icon on your Desktop and see if NTLDR, NTdetect and boot.ini are in the top of the Windows filesytem tree?
It should look like this, [**            A Birds's eye view of Windows XP **(showing the bootloaderfiles)]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")
If you can't find an icon for your Windows partition you might have to [mount your Windows partition]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop") and then take a look. If you have files that are not backed up it would also be a good time to  copy them to another partition or to an external hard drive or to some CD-ROM s. 

A friend of mine who knows more than I do about Windows thinks you can run Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and install your Windows boot files that way. It's worth a try.
Another thing that you might want to try is to [make your own Windows Xp boot floppy disk]("http://support.microsoft.com/kb/305595/EN-US/") with NTLDR, NTdetect and boot.ini on the floppy disk. That will often boot Windows when all else fails. You can even edit the boot.ini from Linux as required because the floppy disk is fat32. So there is some hope. :)

But I think you will have to rescue all your files and delete Windows, delete Ubuntu and re-install Windows in a primary partition. Ubuntu is able to boot in either a primary or a logical partition without any problems at all. You can install Windows where Ubuntu is now, and install Ubuntu where Windows is, then they both should be able to boot up okay.

Sorry about that, but it's Windows' fault, not Ubuntu's.
Try to boot Windows if you can though, let me know if you can, then I can help others with the same problem later. Last time we couldn't fix it, or at least the person with the problem didn't let me know if it was able to be fixed. (Sorry). :(

Regards, Herman

---

