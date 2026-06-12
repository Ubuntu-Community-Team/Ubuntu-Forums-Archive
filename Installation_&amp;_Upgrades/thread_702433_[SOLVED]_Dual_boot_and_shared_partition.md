---
title: "[SOLVED] Dual boot and shared partition"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Arrgoss on 2008-02-20
Hello,
I have read a couple of posts about this matter, but still I would appreciate some help. It's effectively the first time I install Ubuntu, and I want to do it on a laptop with Windows XP already installed. I'd like to have a dual boot with a separate shared partition for all my data and files.

I have 100 GB of hard disk and 2GB of memory (and a dual processor, so I'm installing Ubuntu 7.10 Desktop Ed. AMD64). My questions are what size do you advice me for each partition, and what kind of formatting is best for the shared one? I would use NTFS or FAT32, but for some reason NTFS was not given as an option when I was dealing with the partitioner. Another issue is whether they all should be logical or it doesn't really matter?

Thanks in advance!

---

### Post by benfindlay on 2008-02-20
Hi there,
Linux and NTFS historically do not mix well. It is striaght forward enough to read from an ntfs drive, but writing to it is a different matter. There are various drivers availabe such as ntfs-3g that enable writing to an ntfs drive, but they all provide sketchy wirte capabilities. You can also install extended file support into windows which would allow you to write to the linux drives, but this again doesn't just work. You have to set the drives in control panel every time you boot up I believe.

My personal preference would be to use a fat32 shared partition to store files, although this then imposes a 4 gigabyte file size limit per file stored on it. But this is only really a problem if you're storing huge long (or High resolution) videos.

I wouldn't worry about any fancy settings like logical partitioning, just format them!

In terms of size, it depends how much you will be using each operating system. If you're keeping very litle in windows then you wont need much space for it.

Hope this helps!

---

### Post by Arrgoss on 2008-02-20
Thanks, Benfindlay, it indeed helps! I'll go for FAT32 then (the limit of 4GB per file is not a problem). Is there anything I should know for using the shared folder without problems?

About the size for each partition, I'd like to keep as much as possible for the shared folder, but I will be using fairly both OS. Any indication of what would be a sensitive compromise?

Thanks.

---

### Post by Nameless_one on 2008-02-20
You can avoid FAT by using the [installable ext2 driver for Windows](http://www.fs-driver.org/). The only problem so far (and I have been using it for a long time), is that it is not compatible with Unicode, so if you have filenames in a copdepage other than latin1, they will appear as gibberish (but will still be accessible).

---

### Post by Arrgoss on 2008-02-20
Hi,

Is there any reason I'd want to avoid FAT?

---

### Post by louieb on 2008-02-20
> **Arrgoss said:**
> ...About the size for each partition, I'd like to keep as much as possible for the shared folder...

I've got a basic XP home install on an 8GB drive. Takes about 4-5GB.
XP Pro with Office 2003 takes less that 10GB on my laptop - its in a 14GB partition. 

I size my OS partitions so that there about 50%-60% used and think about giving them more space when they hit 70%-75% used.  

It used to be good advise to make the shared partition fat32. But 2 things have changed my mind about that. 1st is both NTFS and ext3 are much better file systems. and 2nd Linux's ability to write to NTFS has improved over the last couple of years.  Now I format my shared partitions ext3. Would use NTFS but I don't use windows all that much.

---

### Post by froy02 on 2008-02-20
I use NTFS for my shared partitons because linux support for it is now good and also for the following reasons.

Fat16-limited to 2gb per file; files stored in 16kb cluster, meaning a file of 1 byte is still stored with a file size of 16kb or a 16001 byte file is stored as 32kb file.

Fat32-limited to 4gb per file; files stored in 32kb cluster, meaning a 1 byte file would consume 32kb of hard drive space and a 32001 byte file would consume 64kb of disk space.

NTFS- file size limit, in the terabytes count; cluster size is 4kb,meaning a 1 byte file would only consume 4kb space compared to 32kb for fat32 or 16kb for fat16, much more efficient in use of disk space.

---

### Post by Arrgoss on 2008-02-20
I see... But I could not choose that partition as NTFS when I was installing Ubuntu; any reason why? If I want now to change it from FAT32 to NTFS, can I do it without reinstalling everything?

---

### Post by dstew on 2008-02-20
Can the installer format a NTFS? I am not sure it can. If the partition is not already NTFS, you probably need to format it from Windows. If the partition doesn't have anything on it, just delete it and then create and format the partition in Windows. If it has stuff on it, back it up, then format.

---

### Post by Nameless_one on 2008-02-20
The package ntfsprogs has a tool 'mkntfs', which can format a disk with NTFS (probably emptying it though).

---

### Post by louieb on 2008-02-20
> **Arrgoss said:**
> I see... But I could not choose that partition as NTFS when I was installing Ubuntu; any reason why? If I want now to change it from FAT32 to NTFS, can I do it without reinstalling everything?

A Linux installation goes in a partition formated with an open source file system such as ext3 (default and what I use). Thats why the installer does not have an option for NTFS.

If you have a  partition that you want to change from fat to NTFS the imho best way to do partition work is to use GParted on the System Rescue CD. Gparted is also on the Ubuntu live CD.  Be warned that reformatting a partition will destroy any data on that partition.

---

### Post by Arrgoss on 2008-02-21
I finally reformatted the partition from fat to ntfs from windows (didn't read the post that advised me GParted).It seems to work very fine: I can access, read, and write on it from both systems. Thanks!
My only question now is the following: When I access the partition from Ubuntu, it requests my administrator password (at least the first time I access it). How can I change the permissions (owner)? Or is there any reason why I shouldn't?

---

### Post by froy02 on 2008-02-21
> **Arrgoss said:**
> I finally reformatted the partition from fat to ntfs from windows (didn't read the post that advised me GParted).It seems to work very fine: I can access, read, and write on it from both systems. Thanks!
My only question now is the following: When I access the partition from Ubuntu, it requests my administrator password (at least the first time I access it). How can I change the permissions (owner)? Or is there any reason why I shouldn't?

Go to Synaptics Package Manager and install 'ntfs-config'. This would install a little program in your System tools called 'NTFS Configuration Tool'.  Run it and it will show you the drives/partitions that you can mount and stay mounted when you boot up.  Choose the partition you want mounted and it will be mounted whenever you boot up.

---

### Post by Arrgoss on 2008-02-21
Thanks, it works :)

---

