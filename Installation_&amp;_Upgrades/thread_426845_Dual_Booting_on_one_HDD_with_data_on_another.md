---
title: "Dual Booting on one HDD with data on another"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by WATERBOYsh on 2007-04-28
My question here is not about how to set up a dual boot system... I'm sure I could do that (with a guide just to make sure I don't screw something up). I've been using Ubuntu on my laptop for a long time and want to dual boot with Windows XP on my desktop. I'm downloading the X64 version of Ubuntu right now with bittorrent. Right now I have two hard drives in my computer (C (300 gig) and F (20 gig) drives) I use the big 300 gig for Windows and all the applications I install and the small 20 gig for saving all my data so that if the OS crashes I still have my data. I want to split the 300 gig HDD into two partitions, but I need both partitions to be able to fully use the 20 gig drive. They need to be able to read, write, and modify any file on the hard drive. I know that Windows and Linux do not use the same filesystem, so I do not know if this will be possible or not. While I'm at it, I don't know how to change the default home path so that it would be on the 20 gig drive. Any and all suggestions are welcome.

---

### Post by nebousuru on 2007-04-29
> **WATERBOYsh said:**
> My question here is not about how to set up a dual boot system... I'm sure I could do that (with a guide just to make sure I don't screw something up). I've been using Ubuntu on my laptop for a long time and want to dual boot with Windows XP on my desktop. I'm downloading the X64 version of Ubuntu right now with bittorrent. Right now I have two hard drives in my computer (C (300 gig) and F (20 gig) drives) I use the big 300 gig for Windows and all the applications I install and the small 20 gig for saving all my data so that if the OS crashes I still have my data. I want to split the 300 gig HDD into two partitions, but I need both partitions to be able to fully use the 20 gig drive. They need to be able to read, write, and modify any file on the hard drive. I know that Windows and Linux do not use the same filesystem, so I do not know if this will be possible or not. While I'm at it, I don't know how to change the default home path so that it would be on the 20 gig drive. Any and all suggestions are welcome.



If you format the 20GB drive with the fat filesystem, both linux and XP will be able to read/write to it.  I hear linux has problems with ntfs though, but i've never tried.

if you want to use the 20GB drive as your /home directory you should be able to by selecting something like "manually configure partitions" when installing linux, and then creating/selecting partitions as "/" and "/home", etc.  I don't know how good of an idea it is to have the /home directory on a fat partition, though.  I think the permission settings would get wacky.

if you wanted your /home directory on the 20GB drive i would put a second (ext3) partition on it too.  while you are partitioning it would be a good idea to add a swap partition, too.

---

