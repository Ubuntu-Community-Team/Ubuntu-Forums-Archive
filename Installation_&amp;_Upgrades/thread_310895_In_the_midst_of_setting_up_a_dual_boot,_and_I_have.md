---
title: "In the midst of setting up a dual boot, and I have a few questions."
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by Vasant56 on 2006-12-02
Hi, I'm running a Thinkpad T42 with 40gb of space, and am in the midst of setting up a dual boot now.

I've used linux briefly in the past, and although i'm fairly computer literate some of this stuff is fairly new to me. I've decided to migrate to linux for the programming benefits.

Anyways, I decided to split my HD up as 10gb-XP, 10gb-Ubuntu, 20gb-data, all on Fat. I understand XP runs better on NTFS, but I wouldn't be able to write on a NTFS drive. I know i can always switch to NTFS (but not back), but would you guys recommend switching up? 

Also, when I install software, should I install them on my fat32 data drive or on their respective OS drives, and save my data drive for just documents and what not?

And is it easy to resize the partitions later if I need to?

Thanks a lot!

---

### Post by moffa on 2006-12-02
I think you should switch to a NTFS partition.  NTFS-3g allows you to write to NTFS partitions. It seems to work pretty well in terms of reliability not performance.  Keep in mind it may not be perfect so keep backups of data.

Install programs to their respective OS.

---

### Post by Digicrat on 2006-12-02
Depending on what you plan on using it for, I would make the XP partition at least 15-20GB.  Windows tends to eat up a lot more space than a full Linux install.

I have on my laptop 20GB for XP (NTFS), 5GB for shared data (FAT32), and about 10-15GB for Linux.  Not necessarily the best division, but it's worked for me.

As a matter of reliability, I wouldn't let one operating system directly access the installation partition of the other, regardless of it's capabilities.  

I would put all of your data and documents on the shared data partition.  Most programs should be installed to their native OS partition.  

Exceptions would be small programs that you might run under either system (such as certain utilities you might use under Wine in Linux as well as natively in Windows).  If you decide to install any large applications, such as games, that you want to run under either OS, you may want to put parts of it on the data partition.  For example, with UT2k4 on my desktop I have the system (executable) directories installed seperately on the native OS partitions, but moved the larger directories containing game data and maps to a shared partition to save space.

---

### Post by Herman on 2006-12-02
> I understand XP runs better on NTFS, but I wouldn't be able to write on a NTFS drive. I know i can always switch to NTFS (but not back), but would you guys recommend switching up? In my opinion, FAT32 is much more convenient when we are dual booting with Linux. You can both read and write directly to files in Windows from Linux that way, so you don't need as many partitions. The more partitions you have the more space gets wasted because a partition always needs to be larger than the data in it. 
NTFS is useful if you need to work with large files over 4 GB, such as DVDs or the like. But for all other purposes as far as working with files in Windows from Linux is concerned, it's a darned nuisance of a file system.  I keep well away from it.
I agree with moffa though, I have read that NTFS-3g is getting good and in that case NTFS will be alright. I haven't tested NTFS-3g myself, so I don't know.


> Also, when I install software, should I install them on my fat32 data drive or on their respective OS drives, and save my data drive for just documents and what not? You won't be able to download just any old software from the internet and clickon an automatic installer file to install it, Linux doesn't allow users to do that. That's just one of the reasons why Linux is immune from viruses and spyware. You will find plenty of great, free software you can install from the repositories though. Don't worry, it's easy, it's a much better way to do things. :D
>  And is it easy to resize the partitions later if I need to? Yes, I wouldn't lose any sleep worry about which partition needs to be a certian size, just make them any size you like and go ahead and get on with your installation. You can easily adjust the partition sizes very easily later on if you use a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php").

Regards, Herman :D

---

