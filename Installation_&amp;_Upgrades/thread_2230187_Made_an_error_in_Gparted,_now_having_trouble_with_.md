---
title: "Made an error in Gparted, now having trouble with GRUB"
date: 2014-06-17
forum: Installation &amp; Upgrades
---

### Post by courtneyking1990 on 2014-06-17
Let's start from the beginning. 

The computer that I'm trying to fix is a Toshiba Satellite M55-S139. It's about 7-8 years old. It had gotten to the point where it was running slow. I had just discovered Linux and Ubuntu and installed it on my personal computer (the one I'm typing on now). Works great, no issues, perfect. We still kept the old laptop and my parents use it. I decided to install it on the older computer since people had said that it works great on old computers. It didn't. It was way too slow and my parents couldn't get anything done. 

I tried to install Windows XP back on the computer but the .iso file was no good. I tried DSL which did good on it, but my folks can barely see the font and it wasn't very user-friendly. I had partitioned the hard drive according to a tutorial I found on the next and had it split into three parts. I tried Puppy Linux and it worked wonderfully so I wanted to install it to the hard drive so I could still retain my USB drive. I was using Gparted and deleted all of the partitions so I could re-distribute according to a tutorial. 

There was nothing on the hard disk I wanted to save and I started re-partitioning. Well I accidentally made one too big and I stopped the process before it could finish creating this new partition, thinking I could just re-adjust the size and then start over. After I did that it started scanning and wouldn't stop, I logged off Puppy Linux and thought I could start again. When I did this, Puppy got stuck in searching for Puppy files and now it won't go past that point. If I take out the USB then it boots straight to the hard drive and shows this on the screen:

```
GRUB Loading stage1.5.

GRUB loading, please wait...

Error 17
```


What I did was stupid and I'm kicking myself now, but is there anyway to fix it? Here's some more info on the computer, I don't know if it's useful but I got it from the BIOS:

```
Hard Disk: Fujitsu MHV2080AH - (PM)
System Memory: 634 KB
Extended Memory: 446 MB
BIOS Version: 1.10
```

These are three cheat codes I used to try to get Puppy to boot, they didn't work:

```
puppy pfix=noacpi
puppy pfix=acpiforce
puppy pfix=ram
puppy pfix=nox
```

If you need anymore information, just let me know and I'll tell you.

---

### Post by courtneyking1990 on 2014-06-17
Apparently the available partions are:

0300 78150744 hda driver: ide-gd
0301 78019672 hda1 <lots of 0's>hda1

Found this by trying to run the USB with Slitaz on it, and it giving me the Kernal panic error.

---

### Post by Bashing-om on 2014-06-17
courtneyking1990; Hi !

You have not said, but have you considered to use GParted and wipe the hard drive. Start all over from scratch. As I read your post there is nothing to loose by wiping the drive and all to gain.

If you can install more ram, get it up to a meg or more, 
>  from the spec sheet:
Max RAM Supported 2 GB

should be able to run (L)ubuntu . Not that there is a thing wrong with DSL or puppy in my book, I just like, more familiar with, (L)ubuntu.

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2014-06-17
I used to run into "stage 1.5 errors" all the time -- and the details from the linked page helped fix that:  [http://www.supergrubdisk.org/wiki/WindowsErasesGrub]("http://www.supergrubdisk.org/wiki/WindowsErasesGrub")

---

### Post by courtneyking1990 on 2014-06-17
@ Bashing: Yes, that's what I wanted to do with Gparted. But now I can't even get Puppy to boot all the way so I can't even get to Gparted. I used Unetbootin to download and make the USB bootable but it put an old version on there. I'm downloading the latest now. Hopefully of works. 

I dont know how to install RAM, I wouldve loved an Ubuntu flavor on it though. 

@Mark
Where do I put in the commands? All I get is beeping noises when I try to type anything.

---

### Post by courtneyking1990 on 2014-06-17
The updated version of Puppy worked! It's booted now! Should I still try to install to hard drive and partition or just leave it be?

---

### Post by courtneyking1990 on 2014-06-17
Still having problems in Gparted though. It keeps "scanning for devices" and does nothing.

---

### Post by gedakc on 2014-06-18
Assuming that you do not need any of the data on the hard drive, you might try overwritting the partition table with zeroes.  After that you could use GParted to create new partitions and file systems.

The steps to do this are:

1)  Determine the device path for the hard drive to erase.  These are paths like /dev/sd[a-z] on newer GNU/Linux, and /dev/hd[a-z] on older GNU/Linux IDE drives.  It is critically important to identify the correct drive because we will be wiping out the partition table.

2)  Overwrite the initial sectors on the drive:

[FONT=Courier New]sudo dd if=/dev/zero of=***/path-to-hard-drive-to-wipe*** bs=512 count=63[/FONT]

Where ***/path-to-hard-drive-to-wipe*** is something like /dev/sde

The count of 63 was chosen because MBR/MSDOS partition tables use the first 63 sectors for the partition table and boot code.  The MSDOS partition table is actually stored in the first sector of the drive.

---

### Post by Bashing-om on 2014-06-18
courtneyking1990; Hello;

+1 to gedakc's advise. Be aware 'dd' is nicked named 'disk destroyer' for a reason. Be very very sure of what you are telling 'dd' to do. 'dd' Is very literal; will do exactly what is told - even when what you told 'dd' to do is not what you had intended, and, there is no forgiveness for a mistake, and no reversing it once you hit that enter key.
Before invoking 'dd' run terminal commands:
```

sudo fdisk -lu ## for legacy partitioning (MBR)##
##or##
sudo gdisk -l /dev/sda ##for current partitioning (GPT)##
sudo gdisk -l /dev/sdb

```
Do in terminal:
```

man dd

```
for the full disclosure of 'dd'
Again, be very sure of what disk you are operating on as the system has identified that device !

[INDENT][INDENT]careful
[INDENT][INDENT][INDENT]is no accident
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

