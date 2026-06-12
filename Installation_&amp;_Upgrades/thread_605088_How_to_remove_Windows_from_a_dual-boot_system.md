---
title: "How to remove Windows from a dual-boot system?"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by jstevans on 2007-11-06
Hi,

I installed Ubuntu onto an old and beloved laptop that had an existing Windows 2000 Professional installation.  In other words, I created a dual-boot system with both OS on the single partition.   I know, that was dumb.  

I like Ubuntu and want to keep it so I want to eliminate the Windows 2000 install (the hard drive is tiny, 9GB).  

- The Windows install is NOT on a separate partition
- The laptop has no CD or floppy (the first broke, the second is long lost)
- The laptop does not support netboot
- The laptop connects to my network just fine
- It also has a USB port that reads my flash drive

I think getting rid of the Windows install is a matter of deleting all its files and modifying boot.ini but I am not sure.  

Can anyone give me some help as to how to eliminate Windows from this machine without needing to boot from a CD or floppy or network without using a floppy or CD?  

Or, maybe someone can tell me how to add netboot capability to this old soldier?

Thanks.

Jay

---

### Post by bulldog on 2007-11-06
Hmm the same partition you say?
In my understanding ubuntu uses the ext3 file system and windows NTFS or FAT32 so I can't believe what you're telling.

In Ubuntu is a tool named gparted,you can run this and delete the windows partition,because I think you mean installed on the same hdd not in the same partition.
Correct me if I'm wrong however,I like to learn new things too.

---

### Post by jstevans on 2007-11-06
Thank you for the reply.  Perhaps I am using the terms wrong but there is only one hard drive and it is "C:"  My understanding is that if there were a second partition it would be appear in the OS as a D: drive even though it is on the same physical drive.

When I have used Partition Magic to partition drives within Windows (in the past) the new partition always showed up as a D: drive, at least that's how I remember it.

In my case the C: drive has all the normal Windows 2000 folders (including WinNT) and a folder labeled WUBI.

Any idea how I can get rid of Windows 2000 and still boot from Ubuntu?

---

### Post by bulldog on 2007-11-06
Here I'm lost,I know there's a windows installer for ubuntu called wubi,but I have no idea how it works,never got into it.
So I can't really help you with this,because I simply don't know.
Try a search for wubi at the forums or google,maybe you find something useful.

---

