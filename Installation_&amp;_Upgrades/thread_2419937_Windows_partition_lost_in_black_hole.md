---
title: "Windows partition lost in black hole?"
date: 2019-05-27
forum: Installation &amp; Upgrades
---

### Post by linusband on 2019-05-27
Hi all,

I wanted to add an Ubuntu partition to my Windows 10 machine. The Ubuntu  install was successful, but upon rebooting I cannot boot to Windows 10  anymore! In fact, there appears to be no trace  of Windows whatsoever.  My machine has 1TB of space, of which I allocated almost 250GB to  Ubuntu. Ubuntu can see its own partition and recognises that the machine  has 1TB in total, but there is no indication that the other 750GBs  contain Windows 10.
So, like a black hole, the absence of information might show that Windows is there. That's the joke... 
I had a look at posts outlining similar problems, but in those there was always some trace of Windows left in Ubuntu. 
I ran boot-repair and here is the info it gave to me on pastebin: [http://paste.ubuntu.com/p/j96wh6DbZP/](http://paste.ubuntu.com/p/j96wh6DbZP/) 
Any help would be greatly appreciated.

Best,
Linus

---

### Post by ubfan1 on 2019-05-27
It looks like you made a new partition table and created your new partitions instead of shrinking an existing partition (to make unallocated space) and adding new partitions in the unallocated space. I hope you have backups of whatever was originally on the disk.  There might still be data on the disk after 400G, which might be recoverable with disk recovery tools, but if the new install formatted the new partitions, that space is unrecoverable.

---

### Post by yancek on 2019-05-27
I expect you didn't read the Ubuntu documentation on this process at the link below?  Would have save a lot of trouble.  If you have a windows installation DVD and want to try again, it would be good to read it.  Useful information in any case.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by linusband on 2019-05-28
Yes, that is in fact what I did. I was following a walkthrough and foolishly didn't consult the official documentation. If my memory serves me right, I was not able to shrink an existing partition during installation and therefore made a new partition table. 
Luckily I did make backups of the most important files, so I'm happily working on the Ubuntu section now while GParted is slowly sifting through the 750gigs of unknown territory.
Thanks a lot for the speedy response: let this be a learning moment for me.

---

### Post by Rubi1200 on 2019-05-28
What are you trying to do with GParted if I may ask?

---

### Post by linusband on 2019-05-28
I *think* I'm analysing the disk for any traces of Windows.

---

### Post by Rubi1200 on 2019-05-28
Dear linusband,

We've all been there before at some point and made a mistake.

Your Windows installation is gone and GParted will not help you get it back. GParted is a partitioning tool not a file or operating system recovery tool. Even if you had such software I think it highly unlikely you can recover Windows since too much data has probably already been written to the disk.

The script you posted before shows this [https://prnt.sc/nufzmw](https://prnt.sc/nufzmw)

There is no sign of Windows there and what you are doing now will not help, sorry to say this.

If you have the Windows installation disk you can reinstall Windows.

Even if you do not have the Windows disk as long as you have a valid licence and product key you can download and create a bootable disk to reinstall Windows.

Once you have reinstalled we can guide you through the correct way to install Ubuntu as a dual-boot system such that both systems can live happily side by side.

---

### Post by oldfred on 2019-05-28
You probably left Windows fast start up on which sets the hibernation flag. That prevent the Linux NTFS driver from fully seeing the NTFS partition(s) and then the installer will not know you have Windows.

Always turn off fast start up in Windows & use Windows to shrink NTFS partitions, so you have unallocated space to install Ubuntu into.

Testdisk may show some older partitions, but since you installed Ubuntu into the Windows space, you cannot recover them. Some files may be recoverable as Windows NTFS writes to beginning of a "drive", but Linux randomly writes into the entire partition. And Ubuntu is a lot smaller than Windows. You then may be able to use tools like photorec to find files on a drive. But it finds everything, but only by extension, it does not know file name.  Some have posted Windows tools may work better for file recovery on NTFS partitions, but most better ones are not free.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

But if you have a current backup, then not really worth effort to try to recover files. It took me all night to run photorec on a smallish drive. Then weeks comparing files to bit older backup, to see if I could recover some of the newer data. But it recovered older files that were deleted, as well. I had saved  some many times, so many copies to compare.

---

### Post by linusband on 2019-05-29
> **oldfred said:**
> You probably left Windows fast start up on which sets the hibernation flag. That prevent the Linux NTFS driver from fully seeing the NTFS partition(s) and then the installer will not know you have Windows.

Always turn off fast start up in Windows & use Windows to shrink NTFS partitions, so you have unallocated space to install Ubuntu into.
Ah, the guide did say that I could make a partition via Windows as well. Should have done that! (and turned off fast start up of course...). Thanks!

> **Rubi1200 said:**
> Once you have reinstalled we can guide you through the correct way to install Ubuntu as a dual-boot system such that both systems can live happily side by side.

Thank you very much for the offer! Now that Windows is gone I don't mind that much, to be honest. It's freeing, really.
Any tips for me when I want to annex the 750GB digital graveyard into my Ubuntu partition? Just to be sure that I don't mess up again :P

---

### Post by oldfred on 2019-05-29
If you did not make a separate /home you could make that as /home.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

The advantage of creating /home during install is that it then is mounted, has a mount  point and default ownership & permissions.
If you add your own data partition into fstab (if drive is internal) then you have to create mount point, add entry to fstab to mount it and give yourself ownership & permissions to use it.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

If partition is NTFS, you need to either have Windows or at least a Windows repair disk. Windows NTFS will  need chkdsk & defrag and perhaps other maintenance that you cannot do from Linux.

---

