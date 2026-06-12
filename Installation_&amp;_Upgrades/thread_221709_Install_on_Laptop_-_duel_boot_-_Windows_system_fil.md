---
title: "Install on Laptop - duel boot - Windows system files will not move"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by JimS on 2006-07-23
...
After several months using Breezy on my desktop pc, now I would
like to install Dapper on my laptop.  But I seem to have a problem.
I've tried to defrag the laptop's HD, but there are a lot of
"unmoveable" files scattered all thru the HD.

I want to keep Windows XP on the laptop for one program that I still
have not been able to use in Linux.  Therefore I need to be able
to partition the HD and duel boot.

Here is the problem:
How do I compact the HD so all Windows files are at one end,
leaving enought room for Linux?  The HD is plenty big enough
for both.

I thought that I might backup everything using Norton Ghost to
download and then upload all my HD files, and maybe the upload
would compact the HD.  Anyone know about Ghost?
I did the download on my desktop pc that had 2 HDs, but my laptop
has only one.  I could copy to CDs, but I don't know if that would work.
I don't want to buy an external HD.
I do not have copy of my Windows OS disk.
...

---

### Post by john_spiral on 2006-07-24
Is your windows hd FAT or NTFS formatted? 

You could try booting from a live linux CD to run a program like qtparted to partition your drive, I'm not sure how well to handles NTFS formatted partitions, anyone else? 

The Knoppix Live CD has a large collection of disc partition tools, remember to right click the mounted drive on the desktop to set the  access level under Knoppix.

---

### Post by timetunnel on 2006-07-24
> **JimS said:**
> ...
How do I compact the HD so all Windows files are at one end,
leaving enought room for Linux?  The HD is plenty big enough
for both.

Try PageDefrag 
[http://www.sysinternals.com/utilities/pagedefrag.html](http://www.sysinternals.com/utilities/pagedefrag.html)
to defrag some special system files.

> 
I thought that I might backup everything using Norton Ghost to
download and then upload all my HD files, and maybe the upload
would compact the HD.  Anyone know about Ghost?

Making a backup of your partitions is generally highly recommended before fiddling around with the paritions, especially if you don't have anything to re-install it. I've never used Norton stuff but always heard bad things about it. Best tool for making Windows disk images at the moment seems to be Acronis True Image. However, if you have a FAT32 partition, using the Linux tool "partimage" is sufficient (it is included in most Live-CDs, like Knoppix e.g). The status for NTFS is only "experimental" in partimage, so you'd use it at your own "risk".

---

