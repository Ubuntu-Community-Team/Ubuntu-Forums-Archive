---
title: "how to install mount point on new 14.04 installation on external hard drive"
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by mark allyn on 2015-08-17
Hello everyone,

Perhaps the following will sound somewhat goofy and inefficient.  I certainly think it does.  Nevertheless, I have been struggling for two days to install 14.04 on an external hard drive (Seagate 2 TB drive--a work of magic) and that little rodeo has led to my question.  
 
As you will see, I am trying to bypass the initial phases of using the  install disk to partition the drive prior to installing the distro.  

Let us imagine (if we can) that I create a new partition for ext4, and swap on the Seagate external hard drive, but not using the 14.04 install disk, using fdisk and mke2fs instead.  Suppose I now want to somehow identify the partitions on the external hard drive as / and swap partitions so that I can jump immediately to "install" after hitting "something else".  Is this possible? Is there a utility that can do this?  


Thanks,
Mark Allyn

---

### Post by Bashing-om on 2015-08-17
mark allyn; Hello;

Though I may not follow the logic in what you want to accomplish;
'tune2fs'  will label partitions for you .
see:
```

man tune2fs

```

[INDENT][INDENT]hope this helps just a bit
[/INDENT][/INDENT]

---

### Post by TheFu on 2015-08-17
For large disks, it is best to use
* GPT partition tables - not MBR/MSDOS
* fdisk has "issues" with GPT **and** large disks.  Use either parted or gparted.
* I suspect you want more partitions than just 2, especially on a 2TB drive.  I'd go with 
/ 25G
/home 50G 
swap - 4G ... generally more isn't needed unless hibernation or encryption are used or you are running a shared server and don't like your clients much.
/opt - 20G ... perhaps larger if some programs insist
/var - 20G ... perhaps larger if you use virtual machines

I'd leave the rest unused until it is needed. It is hard to predict where more storage is required during an install. If you use LVM, then you can be extremely flexible - well beyond what GPT allows.  Think of LVM as dynamic partitions that can change size without rebooting. Pretty sweet!  MBR has some serious limitations from which GPT relieves us.

Also - be very careful with Seagate drives.  [https://techreport.com/news/27697/latest-backblaze-reliability-data-shows-carnage-for-3tb-seagate-drives](https://techreport.com/news/27697/latest-backblaze-reliability-data-shows-carnage-for-3tb-seagate-drives)  I've been burned by seagate a few times - with a 2TB most recently. Definitely have excellent backups with that drive.

---

### Post by mark allyn on 2015-08-17
Hello Bashing-Om and TheFu

Thanks for responding.  

Bashing:  I will investigate tune2fs.  

The Fu:  Good advice.  You could help me further by giving advice on what mount point to specify on a third partition of this drive that can be used to communicate files between windows and linux.  I have been thinking that /home (as a NTFS partition) might be correct, but perhaps /tmp might be better.

Regards,
Mark

---

### Post by Bashing-om on 2015-08-17
mark allyn; Hey :)

For a shared partition, as Windows -without a lot of help - can not read ubuntu's ext4 file system :
> 
 /home (as a NTFS partition) might be correct, but perhaps /tmp might be better.

NO ! You need the file system native to ubuntu as ext4 for /home .

As to the shared partition:
> 
advice on what mount point to specify on a third partition of this drive that can be used to communicate files between windows and linux.

make that partition as NTFS. Native to Windows, that ubuntu also can read and writes to. A mount point is arbitrary where it is created ( /mnt or /media/usrename ). And fine grained permissions to tailor the access rights can be established in the fstab mount directive.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <- bodhi.zazen -Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[INDENT][INDENT]you are wise
[INDENT][INDENT][INDENT]Prior Prudent Planning Prevents Pi** Poor Performance
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by TheFu on 2015-08-17
Good advice.  Linux cares about file permissions much more than you are used to with Windows. NTFS doesn't support the same permissions as Unix/Linux file systems do, so NTFS cannot be used for /home or **any** location with user HOME directories.  Nothing is hard coded about using /home.  You can put your HOME where you like and every userid can have a different HOME on different storage, provided the permissions model is supported.

/tmp cannot be used either. Unix systems make significant use of /tmp in ways that Windows does NOT. This **is** hard coded.

I wouldn't use /media or /mnt. I've posted the reasons against doing that in these forums in the last few weeks. There is some history for why not.  Any empty directory can be a mount point. If you just want Windows systems to have network access to the storage, use a Linux file system and run samba.  Using NTFS for a samba share complicates things, IMHO.  However, if you need to connect this specific disk to a Windows machine, then NTFS is really the only choice.  It is only useful for media really.  

Programming on a Linux system writing to NTFS just doesn't work for a few reasons. Don't even try java, C, C++ or other compiled languages on NTFS.  Best to use a native Linux file system, then copy over the files you want to the NTFS later. That can be scripted easily with rsync or just use git - much better idea.

---

### Post by mark allyn on 2015-08-18
Good morning, TheFu and Bashing-Om,

Thanks for your detailed responses.  BTW, you mention having written on these matters previously...would it be asking too much if you could let me know where to find them?

Perhaps it would be helpful if I could explain what I want to be able to do.  I want to do most of my work on a linux (14.04) 64 bit box that uses an external (Seagate) drive with the linux partitions.  Occasionally I want to write a file that can be read by a Windows 7 program.  W7 is what resides on the computer's internal hard drive.  Or, less frequently, the other way around.

Does this change your views?

I get that both of you are opposed to making any of the linux mount points NTSF and evidently for very good reasons.  The samba thing might be the right way to go, but I am not familiar with samba as of the moment.  

Regards,
Mark Allyn

---

### Post by TheFu on 2015-08-18
We aren't just against it.  It won't work and doing either will break any Linux system.

Any directory can have a partition added as storage by "mount" or the fstab file. Generally, we want to use empty directories.  It is fine to create a directory where you want storage to be mounted. I do for things that aren't part of the expected OS structure.
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html#The-Root-Directory](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html#The-Root-Directory) explains what and why.

If you need files to be accessible on the same, dual boot, PC then an NTFS partition is the best answer available. Using NTFS for anything other than data (media stuff mainly) files is a bad idea, but for LibreOffice docs, it should be fine assuming you don't care about security at all. 

You can search the forums just like I can. This is a skill worth learning, IMHO, just like learning to read manpages. Use my userid here and *disk layout* or *partitioning* as keywords and it was less than a month ago, but I seem to write the same things over and over the last 5 yrs I've been posting here, so older posts may be helpful for background.  Plus you'll get the context of the answers and what other, smarter, people said too.

---

### Post by mark allyn on 2015-08-19
Hello TheFu,

Thanks for clarifying the precise impact of making /home or other linux system file NTSF.  I avoided a bad mistake.

After thinking the business over, it seems to me the easiest way to do what I want is simply to create a NTSF partition on a plain old USB flash drive and save files to it and then plug it in to W7 after booting up from the internal hard drive.  That is, don't put the NTSF partition on the external hard drive when booting from it.  

From my somewhat cursory research, the W7 machine still won't be able to read the NTSF file on the flash drive.  Evidently, 3rd party software is out there that will do that.  More work to be done.

Thanks for the tip on where to find your previous work.

Regards,
Mark

---

### Post by TheFu on 2015-08-19
Never heard of "NTSF". If you've been searching on that, no surprise that nothing relevant was found.

"NTFS" is the file system.  Details matter, especially on Unix system.

Win7 will read USB NTFS partitions just fine - doesn't matter if flash storage, spinning disk storage or SSD storage is used. No 3rd party software needed.

---

### Post by mark allyn on 2015-08-19
TheFu,

Yup, managed to invert two of the characters.  No, I haven't been searching on the inversion version.

Look, here's the deal on reading NTFS from MY W7 box.  When I stick the flash drive in the port, even though
 NTSF is installed and readable from linux, the W7 box refuses to read it and insists on reformatting the disk.  If you know a way around it, I'd be thrilled.

Mark

---

### Post by oldfred on 2015-08-19
Is the NTFS partition the first partition on flash drive? Windows seems to only like first partitions on flash drives.

---

### Post by mark allyn on 2015-08-19
TheFu,

Please note the inversion once more on line 4 of my post.

I think it must be that the sequence SF is easier to type than FS....  Try it out for yourself.  I just did and I think I'm right.

Mark

---

### Post by mark allyn on 2015-08-20
Hello TheFu,

This is probably the last word on this subject.  At least, from me.  If the first partition on the USB is NTFS, then Win 7 can indeed read the file created in Ubuntu (although, see below sentence).  If the NTFS partition is NOT the first, then Win 7 will demand that the disk be reformatted with of course data loss.  

If the file was created by for example gedit, then formatting info will be lost when the file is read in Win 7 by notepad.

Regards,
Mark Allyn

---

