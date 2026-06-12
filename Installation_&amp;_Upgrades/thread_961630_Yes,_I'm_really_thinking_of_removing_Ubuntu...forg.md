---
title: "Yes, I'm really thinking of removing Ubuntu...forgive me!"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by Serengaeth on 2008-10-28
Evening everyone... I'm a brand new Ubuntu forum user and already I'm nagging you for help. Typical, eh?
I originally installed Ubuntu on my laptop to see if I liked it... and hey, I did! It's now the only OS on my desktop and we're getting along swimmingly with each other.
Trouble is, I'm now looking to remove the Linux partitions from my laptop and stick to Vista on my laptop. I use it for a lot of music applications that Ubuntu doesn't approve of and the extra space would be handy. I'm looking at the Vista Disk Management software and seeing the following partitions:

8.00 GB
Healthy (Active, EISA Configuration)

HDD (C:)
70.15 GB NTFS
Healthy (Boot, Page File, Crash Dump, Primary Partition)

19.99 GB
Healthy (Primary Partition)

675 MB
Healthy (Primary Partition)

Now, obviously the 70.15GB partition is where Windows and most of my applications and data is lurking, and I'm fairly certain that 8GB partition is my laptop's recovery/repair partition. The question I'm presumtuously putting to you is this; "What do you think the other two partitions are?"
Any advice is much appreciated! In return, I can offer help on... ummm... have any of you ever wanted to learn to beat-match?

---

### Post by dstew on 2008-10-28
Is Ubuntu still on that laptop? If so, open a terminal and do```
sudo fdisk -l
```to get a list of the partitions. If Ubuntu is no longer working, boot an Ubuntu Live CD and open a terminal, and do the same command. Post to the forum the output and we can look at the partitions and try to figure out what you have.

---

### Post by caljohnsmith on 2008-10-28
You could restore the Windows Vista MBR (Master Boot Record) so that you can boot straight into Vista and not through Grub, and then it will be safe to format the 20 GB and 700 MB partitions to NTFS (I assume those are your Ubuntu partitions). If you have your Windows Vista Install CD, just go to the command line and run:
```
bootrec /fixmbr
```
Or if you don't have the Install CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let me know how it goes. :)

---

### Post by Serengaeth on 2008-10-28
Phew! I visited the Ubuntu console and with fdisk -l was able to identify the two partitions as "Linux" and "Extended Linux Swap/Solaris". Both have now been formatted into delicious NTFS for World of Warcraft to keep filling with redundant patch files... when will the madness end!
Thanks, dstew and caljohnsmith!

---

