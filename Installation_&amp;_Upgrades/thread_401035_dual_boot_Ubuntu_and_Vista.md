---
title: "dual boot Ubuntu and Vista"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by drwindow on 2007-04-04
I know this has been asked numerous times but hear me out.

I tried to dual boot XP and Ubuntu and in the end the process decimated my hard drive. I knew there was a risk of this happening so I had backed up everything I had.

I decided to upgrade to Vista. I noticed that Vista has a much better built in partioning application than XP.

Is there a way to shrink volume and create a partition then install Ubuntu without any hitches?

I'm thinking that even if the partitioning is successful and the install works fine there will still be the grub/vista incompatibility issue.

Is there anyway I can install Ubuntu without any hitches on a laptop with Vista?
PS I don't not want to uninstall then reinstall vista. I want to install Ubuntu and make sure it goes without a hitch this time.

---

### Post by MJN on 2007-04-04
Search/browse buttons broke? ;)
 
Posted only yesterday in this very forum...
 
[http://ubuntuforums.org/showthread.php?t=399982](http://ubuntuforums.org/showthread.php?t=399982)
 
You shouldn't have any difficulties (famous last words of course) and Grub ought to spot the Vista partition and give you a boot option for it.
 
Mathew

---

### Post by ssican on 2007-04-04
Using ONE Hard Drive, see this link: [http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)  In this link there are two options: 1)Vista Installed  First and 2)Linux Installed First.
Using TWO Hard Drives, see this links: [http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux](http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux)   and  [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by MJN on 2007-04-04
Vista appears to be already installed, and being a laptop is unlikely to have two hard disks.
 
(Useful links for the record anyway though!)
 
Mathew

---

### Post by jck on 2007-04-05
My laptop has 2 hard drives...of course, one is a 250GB USB...

I just got a Dell Inspiron 1501 w/ 1GB ram and 120GB disk...I don't want to void the warranty by blowing up Vista...so...I got the external and I'm going to try to configure the system to boot GRUB and let me either go into Vista on the on-board disk (default), or Ubuntu on the USB device.

I have to keep Vista anyways...boss told me at work...we'll be developing in Vista/VS .NET 2005 in 2008.  

Looks like I have to press harder for my employer to move to Ubuntu :D

---

### Post by MJN on 2007-04-05
I think you're worrying too much - just go ahead and install on your main drive! If anything's asking for complications it's installing it on an external USB drive....

What's this about the warranty? I'd be very surprised if it was in any way affected by you dual-booting Linux on to it!

Mathew

---

### Post by jck on 2007-04-05
I am scared of Dell, man.  There's no telling what they'd do in voiding the warranty if I told them I can't get to the Vista installation screen.

I tried putting Kubuntu 7.04 Beta 64-bit onto it last night...and...GRUB didn't want to boot when I set it to (hd0).  Now, it might be because the Primary drive has 3 partitions on the base Dell install:

1) a FAT16 partition
2) an NTFS partition (OS)
3) an NTFS partition (Recovery)

Maybe I needed to manually set it to (hd0,1)?

The main disk was seen as /dev/sda, then the Kubuntu was seeing my USB as /dev/sdb and allowing me to partition it and install there and everything...the only thing was after install...GRUB would come up with (trying to remember...it's 6am here) Error 15, I think...but...it would not boot.

I think if I can get the GRUB loader to initialise right, I can get the USB setup to work no problems with this laptop...let Vista remain the default boot OS so that if I don't have the external that it loads without an error...etc.  The install seems flawless...it's just the GRUB install that seems not to be quite right.

You have any pointers to an article about installing *ubuntu to an external USB drive?  Should I use 32 bit instead of 64 bit?  I have noticed that even on 64 bit machines, the 32-bit distros still handle and work better.

I would appreciate any help you can give/recommend.  I am learning all this as fast as I can and trying to help others with what I know.

Cheers.

jck

---

