---
title: "FIle system for &quot;neutral&quot; drive"
date: 2005-08-02
forum: Installation &amp; Upgrades
---

### Post by gingermark on 2005-08-02
Hi there,

First off I should probably do the usual apologies if this has already asked - I did two sepearate searches to check, but this is a big place. If it has been asked if someone could provide a link to that thread that would be great.

I was wondering if someone could recommend a file system that can be read from and written to by both Windows and Kubuntu?

I have two hard drives. I intend to partition one and install both XP and Kubuntu on it. My second drive will have no OS on it, just data - this is the drive which I'm not sure about what file system to use. Obviously Kubuntu can write to a FAT32 drive, so that would be an obvious choice, but I then read there is a driver for Windows to facilitate it reading and writing to ext2 drives. So that got me thinking.

My Windows partition will be small - I will only be using it for a few programs - I will be using Kubuntu 95% of the time. Therefore, I'm looking for a file system that will work "best" with Kubuntu, but that will be at least functional with Windows.

If anyone could recommend anything beyond FAT32 or ext2 that would be great, or indeed if those are the two options, any advice on which to choose would be greatly appreciated.

Many thanks,
gingermark.

---

### Post by dave9191 on 2005-08-02
The best thing to do is to have a "shared" partition thats fat32 where you keep the files that you want both windows and linux to access. You could even put windows onto that. I dont know about windows ext2 drivers. But you really want ext3 or reiseefs for you linux partition. 

I have windows installed on a ntfs partion, a shared fat32 drive for music and pictures and other shared files. And then my linux partitions. Linux can read all partions on the computer and write to everyting apart from ntfs, windows can only read and write ntfs and fat32. 

Dave

---

### Post by gingermark on 2005-08-02
Thanks for the reply.

Effectively that is the set-up I will have, although the "shared" partition will be a separate drive - I figured this was a good idea for back-up purposes. If I need to reinstall the OS, my important data can be saved on the second drive.

Is it true that a file can be a maximum of 4GB under FAT32? Whilst I wouldn't usually expect a file to be that size, I have dealt with archives bigger than that in the past, and that could prove a problem...

---

### Post by dave9191 on 2005-08-02
Yes, 4GB (4Gb minus 1 byte to be exact) is the max file size allowed and 128Gb max size for the partion. If you want to work with huge files you want resierfs :) 

You could split the archives into smaller files, but that might not be an option. If the archieves are backups, then you can get the backup program to output smaller files as opposed to one huge one. 

Dave

---

### Post by albrad84 on 2005-08-04
I was actually trying to figure out the same thing...  So I made a free fat32 partition (using a Windows program), but how do I access it in Linux?  I can't seem to access it (or even find it).  Its not under Computer and the capacity of Filesystem hasn't changed...

Or did I just do the partition wrong.  Do you have to do something special to make it 'shared'?

I'm extrememly new to Linux, so sorry if this is a dumb question

Thanks, though

---

### Post by dave9191 on 2005-08-04
Hey, you need to mount the fat32 partion first before you can use it. Instructions can be found at 

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

Dave

---

