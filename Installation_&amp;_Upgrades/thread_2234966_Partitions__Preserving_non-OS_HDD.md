---
title: "Partitions / Preserving non-OS HDD"
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by brendan10 on 2014-07-18
Hi,

Noob alert. 

Been trying Ubuntu as a Live USB and almost ready to make the big leap from Windows.

Q1:
I plan to instal the OS on my 120GB SSD, where I will then save any applications etc I download.
I heard it's a good idea to make a separate /home partition, to ease any future distro switch. 
So ... how big should I make each partition, given I have 120GB to play with?

Q2:
I also have 2 x 2TB HDDs for media (films, music, etc). NTFS format. 
Will I be able to keep them connected whilst overwriting my windows instal on my SSD, or would it be better to remove them first so there is no chance of them being reformatted during the Ubuntu instal?
And if I do remove them during the instal, will they be able to be read by Ubuntu when I plug them back in? 

Many thanks,

Brendan

---

### Post by TheFu on 2014-07-18
You are asking for opinions when it comes to partition sizes. There aren't any MANDATORY sizes - for example, I run my main desktop on a 15G (total size) partition. I started with 10G 5 yrs ago and have slowly grown.  Of course, there is network-based storage for 10+TB of data, but that isn't needed 99.9999% of the time on the desktop. Anyway - you have lots of options.

I'd allocate 20G for the OS and apps - / (this is overkill).  Then allocate 40G for /home (which is also overkill for emails, docs, pdfs, code) and keep any large files elsewhere ... perhaps on /Data which would get the rest of the storage.  Don't forget you'll want/need a swap partition - 2G or the same size as the RAM in the system, whichever is more. This matters for hibernation so make it a tiny bit larger than the RAM.  Too much swap isn't necessary.

NTFS can be read fine from Linux, but there are many reasons NOT to use it for data that is stored on Linux systems - performance will suck accessing that data (NTFS uses FUSE drivers which are significantly slower than native drivers).  Is there a chance the NTFS partitions could be harmed - yes, but if you are careful about which partitions you install things onto, that is minimal.  If you don't understand sda, sdb, sdc - then unplug.  If you aren't 100% positive of the partition/device names, I'd disconnect the SATA cables during install, then add them back later.

---

### Post by mastablasta on 2014-07-18
the again you can always backup home and reinstall... you should have backups anyway...

/home is kind of like my documents in Windows (or maybe more like the stuff under users). do you usually keeps my documents (or whole users) in a separate parition?

---

### Post by oldfred on 2014-07-18
I started using a d: drive in Windows or maybe it was with DOS, so I usually separate system from data.

My 64GB SSD has two Ubuntu installs, splitting drive. My 12.04 is now 11GB and my not yet fully configured 14.04 install uses 7GB. But I have /home inside / (root) but all data on rotating hard drive mounted at /mnt/data and /mnt/shared. My shared partition is still NTFS although not using XP anymore. I do mount all data partitions in every install so I have the same data even if booting a test install.

You do need to run chkdsk periodically on NTFS partitions. So you need Windows or a Windows repairCD or flash drive if using NTFS with Linux. Linux runs fsck every 40 or 60 reboots on / just to be safe.

---

