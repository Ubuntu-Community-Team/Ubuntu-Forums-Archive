---
title: "After &quot;Restore&quot; of /home or /dev/sda6, OS boots into grub"
date: 2013-06-17
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2013-06-17
On a re-boot to run from the GRUB prompt and try to restore the OS, Xubuntu booted. It has changed the desktop color theme, icons and such as the panel network manager icon, but everything seems OK. Please move on to someone who needs help. thanks.


============= original post below ===============
The OS failed to boot last week. Today, after reformatting the harddrive into / (dev/sda1), /home (dev/sda6), I ran the Restore from the default Ubuntu package named: "Backup" (formerly Deja-Dup). It has restored all the objects in my /home. Hurrah!

However, later today, because I could not install via apt-get, aptitude, or Ubuntu Software Center, I re-booted. That took me to the GRUB 

> 

prompt.

I'm in LiveUSB at the moment and would like some advice before I use "Boot-Repair".

The objects that "Backup" backed up were in a partition that used ext3, or ext4. It is soooo long ago I don't remember which. As I have read where Linus says ext2 is "safer" (not quoting him here), I decided to use ext2 when I reformatted and partitioned the entire 400 gig drive as follows:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x00052a4f

Device Boot     Start         End               Blocks        Id        System
/dev/sda1   *        2048       39063551    19530752   83       Linux
/dev/sda2        39065598   781422591   371178497    5      Extended
/dev/sda5       765798400  781422591     7812096   82       Linux swap / Solaris
/dev/sda6        39065600   765798399   363366400   83     Linux

Did I make a booboo by changing from ext3/4 to ext2?

Would it be simpler to reformat to ext3 and re-partition the drive and then restore the "backup"?

Is there anything else I should know before starting to use Boot-Repair? Maybe this isn't a GRUB problem and I'm confused. The computer community needs a keyword: bootdead to describe what happens when the OS doesn't work in the general manner in which it's coders intendd.

---

