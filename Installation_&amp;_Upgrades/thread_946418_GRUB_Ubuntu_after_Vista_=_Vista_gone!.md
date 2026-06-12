---
title: "GRUB: Ubuntu after Vista = Vista gone!"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by Fleuris on 2008-10-13
Hello,

I've a problem, I have a new PC with a 750GB SATA disk, with 3 partitions on it:

1st partition: 200GB: Windows Vista Ultimate 32-bit (NTFS)
2nd partition: 150GB: Linux Ubuntu 8.10 (Bèta) 32-bit (EXT3)
3rd partition: 400GB: Storage & Backup (NTFS)

First, I installed Vista, then, when the Bèta was released, I installed Ubuntu 8.10 Bèta (it is great btw:guitar:). But the GRUB doesn't show Vista in the list (you know, when the pc boots, you get a screen where you can select the OS you want to boot). I already tried modifying the menu.lst, and reïnstall the GRUB, reïnstall the Windows Boot Loader, overwrite the MBR, etc. But I can't get Vista to boot!!:(

In the 'fresh' menu.lst, there was no Vista at all, and when I do it manually it can't recognize the device. Except when I say the Windows root is (hd0,2). But then 'something' says that bootmngr is missing. Ubuntu 8.10 however is in the list, and boots perfectly.

Both Ubuntu and Vista partitions can be removed (there's no important data on them), but the 3rd partition HAS TO REMAIN WERE IT IS! Only in case of emergency I can back-up the back-ups to another HDD.

I hope you can help me, I use Vista for games, and I game a lot!

Fleuris

---

### Post by adrian15 on 2008-10-13
> **Fleuris said:**
> 
1st partition: 200GB: Windows Vista Ultimate 32-bit (NTFS)
2nd partition: 150GB: Linux Ubuntu 8.10 (Bèta) 32-bit (EXT3)
3rd partition: 400GB: Storage & Backup (NTFS)

But I can't get Vista to boot!!:(



If you are right about Vista being in the first partition check: [http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems#Grub_solution](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems#Grub_solution)

If it still does not work activate the Vista partition from the [Super Grub Disk](http://www.supergrubdisk.org)'s [Boot & Tools](http://www.supergrubdisk.org/wiki/SGD_Basic_Menu#Boot_.26_Tools) -> Activate partitions menu.

If it still does not work please post [Hard Disks partition layout from Super Grub Disk point of view](http://www.supergrubdisk.org/wiki/Support_Rules#Run_partition_layout_option).


adrian15

---

### Post by Fleuris on 2008-10-13
[quote=adrian15]If you are right about Vista being in the first partition check: [http://www.supergrubdisk.org/wiki/Ho...#Grub_solution](http://www.supergrubdisk.org/wiki/Ho...#Grub_solution)

If it still does not work activate the Vista partition from the Super Grub Disk's Boot & Tools -> Activate partitions menu.

If it still does not work please post Hard Disks partition layout from Super Grub Disk point of view.


adrian15[/quote]

I'll try that, thanks!

I've just tried installing Ubuntu 8.04 on another partition, but even that won't work. The GRUB shows both Ubuntu's, but no Windows Vista!

---

### Post by caljohnsmith on 2008-10-13
> **adrian15 said:**
> 
If it still does not work activate the Vista partition from the [Super Grub Disk](http://www.supergrubdisk.org)'s [Boot & Tools](http://www.supergrubdisk.org/wiki/SGD_Basic_Menu#Boot_.26_Tools) -> Activate partitions menu.

adrian15
Just out of curiosity, I followed that link you give above for "activate partitions", and it doesn't say what is does; does it set the boot flag on the partition, i.e. make it the "active" partition?

---

### Post by adrian15 on 2008-10-13
> **caljohnsmith said:**
> Just out of curiosity, I followed that link you give above for "activate partitions", and it doesn't say what is does; does it set the boot flag on the partition, i.e. make it the "active" partition?

Yes, you are right.

---

### Post by adrian15 on 2008-10-13
> **Fleuris said:**
> I'll try that, thanks!

I've just tried installing Ubuntu 8.04 on another partition, but even that won't work. The GRUB shows both Ubuntu's, but no Windows Vista!

Try it and Vista entry will appear. Depending on your setup it might boot or not (multiple hard disk give some headaches sometimes).

adrian15

---

### Post by Fleuris on 2008-10-14
All right, I tried everything you wrote, and nothing has worked!:confused:

I made my menu.lst look like this: (this is my menu.lst)
> ## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2449953c-591f-4d3d-a048-3a216f7755ea ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2449953c-591f-4d3d-a048-3a216f7755ea ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=2449953c-591f-4d3d-a048-3a216f7755ea ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=2449953c-591f-4d3d-a048-3a216f7755ea ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

title           Windows
rootnoverify            (hd0,0)
makeactive
chainloader     +1
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

But when I try to boot Windows, it says: "Error 12: Invalid device requested"

The I tried to activate the partition with my Windows (hd0,4), but then it also says: "Error 12: Invalid device requested" this message is in the SGD.

Now, here is my layout, I hope you can help me out:
> fdisdklu
6 (hd0,5) ext2fs 141GB Ubuntu inteprid (development branch) \n \l
pause SGD has succeeded!
SGD has succeeded!

And here is my overview of my partitions, from SGD:
> N   IDE   SCSI   GRUB   HURD   TYPE   SIZE   OS
3   hda3   sda3   (hd0,2)   hd0s3   NTFS   356GB   Windows
5   hda5   sda5   (hd0,4)   hd0s5   NTFS   195GB   Windows
6   hda6   sda6   (hd0,5)   hd0s6   ext2fs   141GB   Ubuntu inteprid
7   hda7   sda7   (hd0,6)   hd0s7   Swap   4GB   

---

### Post by caljohnsmith on 2008-10-14
It would help if you could post:
```
sudo fdisk -lu
```
Which I assume is what the SGD output you posted is, but it shows your Windows is not on sda1; you have two NTFS partitions, sda3 and sda5 according to SGD. Do you know which one is Vista? Try changing your Windows entry in your menu.lst to:
```
title Windows Vista
rootnoverify (hd0,2)
makeactive
chainloader +1
```
And let me know what happens when you try it on start up. If it doesn't work, please post the output of:
```
sudo mount /dev/sda3 /mnt
ls -l /mnt
```
Note "-l" is a lowercase L, not a one.

---

### Post by adrian15 on 2008-10-14
> **Fleuris said:**
> 
But when I try to boot Windows, it says: "Error 12: Invalid device requested"

Can you please remove the makeactive line and see what it happens?

> **Fleuris said:**
> 
The I tried to activate the partition with my Windows (hd0,4), but then it also says: "Error 12: Invalid device requested" this message is in the SGD.

Interesting.

> **Fleuris said:**
> 
Now, here is my layout, I hope you can help me out:

If you use 0.9766 SGD version I definitely need to fix it because it should show you all the lines and not only one line.

> **Fleuris said:**
> 
And here is my overview of my partitions, from SGD:
From Boot & Tools -> Show Partitions menu, isn't it?

Let's see you can try this on your menu.lst (see that there is not a makeactive command):

```

title win
rootnoverify (hd0,2)
chainloader +1
boot

```

adrian15

---

### Post by Fleuris on 2008-10-14
Here is the result of 'sudo fdisk -lu':

> Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6570e6d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065   716788169   358386052+   f  W95 Ext'd (LBA)
/dev/sda3   *   716802048  1465145343   374171648    7  HPFS/NTFS
/dev/sda5           16128   409593239   204788556    7  HPFS/NTFS
/dev/sda6       409593303   707036714   148721706   83  Linux
/dev/sda7       707036778   716788169     4875696   82  Linux swap / Solaris



result of /mnt:

> total 28
drwxrwxrwx 1 root root     0 2008-10-13 21:55 Backup
drwxrwxrwx 1 root root  4096 2008-10-11 14:40 Bewaar
drwxrwxrwx 1 root root     0 2008-10-13 23:36 Boot
drwxrwxrwx 1 root root 12288 2008-10-12 18:35 Downloads
drwxrwxrwx 1 root root  4096 2008-10-11 12:41 Games
drwxrwxrwx 1 root root     0 2008-10-11 23:10 Muziek
drwxrwxrwx 1 root root     0 2008-10-12 10:12 $RECYCLE.BIN
drwxrwxrwx 1 root root     0 2008-10-11 16:37 RECYCLER
drwxrwxrwx 1 root root  4096 2008-10-11 14:36 System Volume Information
drwxrwxrwx 1 root root  4096 2008-10-12 18:12 Torrent


sda3 is my backup partition, sda5 is the partition with windows vista on it. I already tried 'rootnoverify (hd0,2)', is says that BOOTMNGR is missing, when I reinstall the Vista bootmanager, it doesn't help. But I will try it without 'makeactive'

I'm using the newest version of SGD (downloaded 2 days ago)

I'm now going to try booting without the 'makeactive' command.

---

### Post by Fleuris on 2008-10-14
Hmm, it's getting better...

With (hd0,2) it gives the same error as before, but with (hd0,4) it says: "Starting up...", but then nothing, just nothing, no boot, no PC activity.

Any ideas?:-?

---

### Post by adrian15 on 2008-10-14
> **Fleuris said:**
> sda5 is the partition with windows vista on it.

```

title win
rootnoverify (hd0,4)
chainloader +1
boot

```

If it still does not work try:

```

title win
root (hd0,4)
rootnoverify (hd0,4)
chainloader +1
boot

```

(Yes, both root and rootnoverify lines.)

Is it normal that you have a Vista partition on a logical partition?
Did you delete another Windows partition without telling it to us?

adrian15

---

### Post by adrian15 on 2008-10-14
> **Fleuris said:**
> Hmm, it's getting better...
With (hd0,2) it gives the same error as before, but with (hd0,4) it says: "Starting up...", but then nothing, just nothing, no boot, no PC activity.
Any ideas?:-?

If you get Starting up... from (hd0,4) and nothing more try to fix it from a Windows disk, that fixboot and so on commands.

What about my question about a deleted Windows installation?

adrian15

---

### Post by caljohnsmith on 2008-10-14
Fleuris, to boot Windows Vista from a logical partition is not exactly easy and takes special steps; how did you install Vista to a logical partition to begin with? If you want to see what it will take to boot Vista from a logical partition, I would recommend following this guide:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

[QUOTE=adrian15]```
title win
root (hd0,4)
rootnoverify (hd0,4)
chainloader +1
boot
```

(Yes, both root and rootnoverify lines.)[/QUOTE]
Just curious, but what does using *both* root and rootnoverify do? :) From the Grub manual, I think using only one is necessary, and of course it depends on the case which to use; but is that supposed to be some special trick?

---

### Post by adrian15 on 2008-10-14
> **caljohnsmith said:**
> 
Just curious, but what does using *both* root and rootnoverify do? :)

Well, this fix is for [different hard disks](http://www.mail-archive.com/bug-grub@gnu.org/msg10928.html), however my intuition tells me that with logical partitions it might be useful too.

adrian15

---

### Post by Fleuris on 2008-10-14
I made the Vista partition in Windows Setup, I have really no idea if it is a logical partition or not, altough I know quite a lot about computers:P
With Windows Setup I made three partitions: 1. Windows Vista, 2. Ubuntu, and 3. Backup. When I installed Ubuntu I deleted the 2nd one, Ubuntu, and replaced it with two new one's: Swap (4GB), and Ubuntu (ext3).

I'm now going to try the new Menu.lst, but how do I know if it is a logical partition?

---

### Post by Fleuris on 2008-10-14
double 'root' won't work! again: 'starting up...' and nothing.

I'm gonna check the tread about logical booting:P


EDIT: I can't download the vista boot files, link is not working...:(

---

### Post by adrian15 on 2008-10-15
> **Fleuris said:**
> double 'root' won't work! again: 'starting up...' and nothing.

Ok.
> **Fleuris said:**
> 
I'm gonna check the tread about logical booting:P
(

By the way, did you move the windows partition while repartitioning for making space for your Linux? The windows partition being a logical one is very strange.

adrian15

---

### Post by Fleuris on 2008-10-15
Very starnge indeed;) but I have the solution now, I don't know how or why Vista was instralled on a logical partition, but that is the problem. I just reinstalled vista, on a primary parition this time, and than Ubuntu, and it works!:)

So, never install Vista on a logical partition!:P

Thanks for your help, adrian15 and caljohnsmith!:KS

---

