---
title: "[SOLVED] HELP! win2k screwed my MBR!"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by captainwitherspoon on 2007-08-30
I've been trying to view my ubuntu partition in win2k for a while. I changed some things with some programs in the 'administrative tools' section and it screwed my grub! I booted with the live cd and I can't view my ubuntu partition from that even! I have data I'd like to save but I wouldn't mind reinstalling ubuntu. I ran part of the reinstall program and it seems to be reporting that partition as ntfs but it should be ext3 (I think). I'm not sure what windows changed but I really don't want to lose my data! I didn't format the drive, I was trying to change how windows views it. btw the grub error I get is 'error 17'
I've tried some grub reinstall threads but I can't get them to work. 
Ideally, I'd like to first view the contents of that hd with the livecd to make sure it's all right, then reinstall ubuntu in some way that it doesn't del my data. (is there a way to merge partitions?) AAAAGH! HELP! 
(f you win2k!)

---

### Post by merlinus on 2007-08-30
Try using supergrub to boot linux:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

And when it is fixed, install this driver so you can access ubuntu from windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I have no problems dual-booting ubuntu with win2000 on three computers.

-merlin

---

### Post by captainwitherspoon on 2007-08-30
Thanks for the quick response, I'm downloading it right now. In the mean time, is there a way  to view my files from the livecd? I'm really concerned that win2k ruined my partition, I'd like to make sure it's ok..

---

### Post by mckryptyk on 2007-08-30
Type exactly as is below into terminal to mount your partition. (using livecd)

```
sudo fdisk -l
``` 

Find your partition on the list (ext3 probably)

```
cd ~/Desktop
```

```
mkdir -p ~/Desktop/mydisk 
```

```
sudo mount -t ext3 /dev/"your partition here" ~/Desktop/mydisk
```

```
sudo nautilus ~/Desktop/mydisk
```

Cheers.

---

### Post by merlinus on 2007-08-30
You will have to boot from the live cd and manually mount your ubuntu partition.

```

sudo fdisk -l

```

will show which partition this is.

Then

```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu

```

(substitute the ubuntu partition from fdisk -l for sda2)

Then look for it in Places/Computer/File System/media/ubuntu.

-merlin

---

### Post by captainwitherspoon on 2007-08-30
Here's the output
```
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/hda: 200.0 GB, 200049647616 bytes 
86 heads, 15 sectors/track, 302885 cylinders 
Units = cylinders of 1290 * 512 = 660480 bytes 

   Device Boot      Start         End      Blocks   Id  System 
/dev/hda1   *           1      208090   134217727+   4  FAT16 <32M 

Disk /dev/hda1: 137.4 GB, 137438952960 bytes 
86 heads, 15 sectors/track, 208089 cylinders 
Units = cylinders of 1290 * 512 = 660480 bytes 

     Device Boot      Start         End      Blocks   Id  System 
/dev/hda1p1   *           1      208090   134217727+   4  FAT16 <32M 
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /media/ubuntu 
mount: wrong fs type, bad option, bad superblock on /dev/hda1, 
       missing codepage or other error 
       In some cases useful info is found in syslog - try 
       dmesg | tail  or so 

```
I really think win2k screwed something... I'm almost sure that drive should be ext3 and it wasn't partitioned in 2 before...

Oh, I did create the dir, I didn't show that part but it was done...

---

### Post by merlinus on 2007-08-30
From what I see, there is only one partition, and it is fat16.  The second fdisk -l entry is some sort of duplicate.

You can try to mount it as fat16:

sudo mount -t vfat /dev/hda1 /media/ubuntu

BTW, how were you trying to view the ubuntu partition in windows?  Had you installed fs-driver?

-merlin

---

### Post by captainwitherspoon on 2007-08-30
hrmmm, no dice...
```
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/hda: 200.0 GB, 200049647616 bytes 
86 heads, 15 sectors/track, 302885 cylinders 
Units = cylinders of 1290 * 512 = 660480 bytes 

   Device Boot      Start         End      Blocks   Id  System 
/dev/hda1   *           1      208090   134217727+   4  FAT16 <32M 

Disk /dev/hda1: 137.4 GB, 137438952960 bytes 
86 heads, 15 sectors/track, 208089 cylinders 
Units = cylinders of 1290 * 512 = 660480 bytes 

     Device Boot      Start         End      Blocks   Id  System 
/dev/hda1p1   *           1      208090   134217727+   4  FAT16 <32M 
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu 
ubuntu@ubuntu:~$ sudo mount -t vfat /dev/hda1 /media/ubuntu 
mount: wrong fs type, bad option, bad superblock on /dev/hda1, 
       missing codepage or other error 
       In some cases useful info is found in syslog - try 
       dmesg | tail  or so 

ubuntu@ubuntu:~$ dmesg | tail 
[  164.031111] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed. 
[  165.936694] NET: Registered protocol family 10 
[  165.936798] lo: Disabled Privacy Extensions 
[  173.728900] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed. 
[  198.683938] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed. 
[  222.035771] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed. 
[  245.393937] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed. 
[  270.345161] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed. 
[  294.315658] FAT: invalid media value (0x06) 
[  294.315665] VFS: Can't find a valid FAT filesystem on dev hda1.  
```
Any other ideas? Really appreciate the help so far!

---

### Post by merlinus on 2007-08-30
It certainly seems that the the partition table and/or filesystem is defective.

If you are wanting to try to recover data from it, try this:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

If not, you might try to format it with gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by captainwitherspoon on 2007-08-30
Hey, I got win2k back up, is there some way I can view this drive in that? agh, what a mess...
So far I can't get testdisk to do much, it recovered a bunch of partial files but the data on that disk won't fit on my win2k hd...

---

### Post by captainwitherspoon on 2007-08-30
GOT IT!
The problem was win2k needs to have LBA40 enabled to view drives larger than 137gb. After I enabled that using these instructions [http://support.microsoft.com/kb/305098/en-us](http://support.microsoft.com/kb/305098/en-us) the recovery tool worked perfectly, then fs-driver allowed me to view the contents of the drive. Phew. now I can backup and reinstall. Thanks for the help! I was really boned. :guitar:

---

