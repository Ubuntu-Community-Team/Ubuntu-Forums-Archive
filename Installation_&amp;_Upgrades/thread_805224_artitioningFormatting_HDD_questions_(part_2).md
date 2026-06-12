---
title: "artitioning/Formatting HDD questions (part 2)"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by rptizzle on 2008-05-23
Here's the continuation to my original thread - my keyboard failed, so here's the rest.

What file format does Ubuntu use? When I insert a HDD formatted by Ubuntu on my XP machine, XP detects the drive but can't read it - it immediately asks me if I want to format the drive.

I had hoped that Ubuntu used the NTFS format so that I could swap drives from my Ubuntu machine to my XP machine, at least until I'm comfortable enough with Ubuntu to drop my XP machine. Is there are common file format that I could use?

I also plugged in a second drive that has two partitions (formatted by Ubuntu). Ubuntu shows one partition, but not the other on the desktop. Does anyone know why that is?

Any help is appreciated. Thank you.

- Ricardo

---

### Post by Herman on 2008-05-23
:) Hello rptizzle,
Ubuntu uses the ext3 file system by default, but it can also use just about any file system.

Windows XP can't understand Ubuntu's ext3 file system unless you install special drivers.
I don't know how good those special drivers are now, but I have seen a few posts here where people have tried to use them and had severe ext3 file system damage as a result.

Ubuntu can read and write to either FAT32 or NTFS file systems quite safely these days. Either of those would do for a shared data partition. FAT32 is more stable, but if you're planning on storing large files, such as a DVD movie, then you might need to use NTFS.

It's best to install Ubuntu in one single integral '/' (root) partition plus a small swap area and have a separate data partition that your two operating systems can share rather than having a separate /home for Ubuntu. (Messy and a waste of good disk space).

What kind of 'extra drive' did you plug in? Ubuntu will normally mount any USB device automatically, but if it's an IDE (PATA) or SATA connected hard drive, then you probably need to mount the file systems in it yourself. There are two ways of doing that. If it's just for one session, you can use the mount command method. If you want this hard disk mounted automatically every time you boot up from now on, you can make an entry for it in your /etc/fstab file and that will mean the file systems will be automtically checked at each boot-up, and mounted.

Try reading some of this page for more details, [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm").

Regards, Herman :)

---

### Post by rptizzle on 2008-05-24
Herman,

Thank you for the response.

I'm afraid I may end up installing Vista on this machine for now... until I get more used to Ubuntu which I'll have running on my other machine. I have not been able to get any work done on this machine in the past few days.

That link you sent appears to be a dead link. That site looks nice and I'll explore it.

I'd like to become a Linux expert and be able to tutor others so they can be free too. :)

I am going to search meetup.com for a Linux group in my area so I can meet people in a more personal way. I have not made much progress with Ubuntu yet.

Thanks a lot. 

- Ricardo

---

