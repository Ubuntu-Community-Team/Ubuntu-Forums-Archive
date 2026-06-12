---
title: "no &quot;install alongside&quot; option, cant instal dualboot"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by washichi on 2014-08-08
hi,

I'm trying to install a dualboot on my laptop, but it's not working.
in the past I've done it but I've some weird things now.

laptop setup:
- windows 8.1 64x
- fastboot turned off
- 500GB hdd -> a partition of 75gb unallocated for ubuntu (ElementeryOs)

problem:
when I run the ubuntu, or elementeryOS, setup I cann't choose the option: " install ubuntu alongside windows".
If I choose "something else" to manually select the 75gb unallocated partition, that partition dont show up.
The only thing I see is: unallocated 465,76GB (/dv/sda)
So ubuntu thinks my whole HDD is empty, and unallocated.
Creating a new partition in ubuntu isn't really an option cause it's going to use my whole HDD, and I guess it will then be damaged in windows.

How can I safely use my 75gb partition, or create one in ubuntu?

If you need any logs or something, please tell me in a comment, cause I dont know which log is needed in this case
- I will update my bios settings tomorrow, including pics-

---

### Post by grahammechanical on 2014-08-08
From a live session we can use Gparted to see if that shows the unallocated space. You could also examine the hard disk with a Windows utility. Does that show unallocated space?

Regards.

---

### Post by kansasnoob on 2014-08-08
It's a good thing you stopped:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

I don't know how to work around that :(

---

### Post by washichi on 2014-08-10
> **grahammechanical said:**
> From a live session we can use Gparted to see if that shows the unallocated space. You could also examine the hard disk with a Windows utility. Does that show unallocated space?

Regards.

windows shows the 75 gb unallocated space, gparted doesnt:

I use easyUS to create the partition, it looks like this:
[IMG]http://i60.tinypic.com/ere8oz.png[/IMG]


when I boot Elementery OS in a life session, this is what gparted says:

[http://oi62.tinypic.com/jfg0o1.jpg]("http://i62.tinypic.com/jfg0o1.jpg")


@[COLOR=#000000]kansasnoob, thanks! I will read that post, maybe there is a solution. but I'm afraid not... yet...[/COLOR]

---

### Post by coffeecat on 2014-08-10
@washichi, for Gparted to show "unallocated" and for a Windows tool to show your partitions, almost certainly means that you have a problem in the partition table. I notice you used a Windows 3rd party partitioning tool. That may very well be the culprit. It's best to avoid Windows 3rd party partitioners. Use Windows' Disk Management to shrink or resize your Windows C: partition and Gparted for everything else.

But at the moment you can't use Gparted, so let's see if there is a partition table problem. Boot into the Ubuntu live CD desktop - not into the installer - open a terminal and run this command:

```
sudo fdisk -lu
```

Post the output. You can paste the output into a text editor, or directly into your post if you can get internet access in the live session, by highlighting the output with your mouse -> right-click -> copy, and then paste.

By the way, I've removed the img tags from your giant image to leave the link. Please consider those with limited bandwidth and use the manage attachments button to create thumbnails in your post for images.

---

### Post by washichi on 2014-08-10
result "sudo fdisk -lu" command:

```
 elementary@elementary:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9e4e97d8


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   819491714   409386433+   7  HPFS/NTFS/exFAT


Disk /dev/sdb: 2004 MB, 2004877312 bytes
64 heads, 42 sectors/track, 1456 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3915775     1957872    b  W95 FAT32
elementary@elementary:~$ 

```

---

### Post by coffeecat on 2014-08-10
There wasn't the problem that I thought we might see, but:

> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'!

Yet the screenshot you posted of easeUS tells us that the disk has a mbr partition table, with Unallocated = logical. That latter doesn't make any sense at all. Let's see what parted, the backend to gparted makes of it. Post the output of:

```
sudo parted -l
```

I suggest you use the Ubuntu live session. I have no idea what the Elementary people do with the Ubuntu base when they build their OS. Let's use tools from the OS that is supported here.

It's possible that you have residual GPT data on a mbr disk and that Gparted is being confused by this. I wasn't aware that this was a problem with Gparted, but we may see with the output of parted. There is a utility which can fix this, if this is the case, but let's see the output of parted first.

---

### Post by washichi on 2014-08-12
thank you for your help and time!

I'm now using ubuntu-14.04-desktop-amd64.
(it doesnt support my wifi card :() 

result of the "sudo parted -L command in ubuntu live session:
```
ubuntu@ubuntu:~$ sudo parted -lWarning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?   
```

I didn't press yes/no cause I dont know anything about my partition table, and even dont know what GPT  is :p.
So I'm googling right now. 

I hope you can tell me what I can do best: yes/no

---

### Post by coffeecat on 2014-08-12
Re-reading your first post, I see that you are using a laptop with Windows 8.1. If that was pre-installed Windows 8, then you should have a GPT (GUID partition table) so ignore my comment in post #7 about "residual GPT data on a mbr disk". It's much more likely that you have a corrupted GPT and possibly that your 3rd party partitioning tool caused this.

Rather than recommend a tool to fix this, because I'm not 100% sure, I'll pm someone else to have a look.

---

### Post by oldfred on 2014-08-12
Windows requires gpt partitioning with UEFI boot. And fdisk is only for MBR(msdos) partitioned drives. The protective MBR in gpt partitioning is just for that case where you use fdisk and it will show one large gpt partition, so you do not attempt to repartition with MBR. So gpt is what you need & want. Say yes on parted list or use gdisk to fix partition tables if gpt is corrupted.

sudo apt-get install gdisk
 sudo gdisk -l /dev/sda

    
If you have not rebooted into Windows, do so as after any resize it has to run chkdsk, also make sure fast boot or the always on hibernation is off in Windows. Both chkdsk and hibernation have flags that prevent the Linux NTFS driver from mounting the partition(s) normally. 

       WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

---

### Post by washichi on 2014-08-15
thanks for your help guys, but still no luck:(

I did the following:

booted ubuntu live session > [COLOR=#000000]sudo apt-get install gdisk > [/COLOR][COLOR=#000000]sudo gdisk -l /dev/sda >  : then i choose gpt.
after that I tried to install but still no "install alongside" option, nothing was changed in gparted too.
after a reboot I checked again, but still nothing changed.

[/COLOR]

---

### Post by oldfred on 2014-08-15
Did you reinstall Windows in BIOS/MBR mode, when system was originally UEFI with gpt partitioning.

Windows does not correctly convert to MBR(msdos). It leaves backup gpt partition table and all Linux tools get confused if drive is really MBR or gpt. 

If you have Windows in BIOS with MBR then you have to remove backup gpt table. But do not run fixparts if really UEFI boot.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

