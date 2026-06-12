---
title: "Reinstallation without losing /home?"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by nxn on 2006-12-20
Is there any way to reinstall ubuntu without losing my /home directory if it's not on a separate partition? Right now I'm thinking of deleting everything off of the disk except /home and trying to install again without formatting (not sure if an install like this is even possible). 

I'm doing this because my ubuntu installation is not functional, it wont boot, and I'm not trying to fix it by hand. It's honestly messed up to the point that a manual fix is not an option. ](*,) 

Backing up my data is also too inconveniant since /home is around 60gb, and I don't think I have any spare hard drives with 60gb free anywhere. Any ideas on how to do this?

---

### Post by aysiu on 2006-12-20
No, it's not possible. You need a way to back up your files or a place to move home if you're going to create a separate /home partition.

---

### Post by wpshooter on 2006-12-20
I hope I am wrong but I think you are up a creek without a paddle.

This is why it is very important to partition a separate /home.

---

### Post by nxn on 2006-12-20
I'm not trying to make /home into a separate partition, I'm simply trying to install ubuntu on an existing partition without losing my data on it. The help in the install's partition setup isn't really clear on what will happen when I chose to use an existing partition for my ubuntu install. I'm not sure if the data will be lost or if it will just install with the data there. 

Right now I'm on a breezy live cd about to resize the hda1 partition (the one /home is on) and install ubuntu outside of it.

---

### Post by aysiu on 2006-12-20
[quote=nxn]I'm not trying to make /home into a separate partition, I'm simply trying to install ubuntu on an existing partition without losing my data on it.[/quote]When you install on an existing partition, you **erase** that partition. The only way to preserve the data is to have a separate data or /home partition and install over another partition. That's why people create separate /home partitions--for your exact situation.

> Right now I'm on a breezy live cd about to resize the hda1 partition (the one /home is on) and install ubuntu outside of it. I like the way you're thinking. That may just do it! If you carve out a new 8 GB partition for your reinstallation, you can mount the other partition as a data partition (I call mine /documents) and then symlink the appropriate folders to your /home/nxn directory.

Any reason you're going with Breezy and not Dapper or Edgy?

---

### Post by nxn on 2006-12-20
Gparted actually failed while trying to resize it, I had to do it directly through resize2fs, hopefully my data is still ok.

And heh, yeah, I don't have a dapper or edgy cd, and I left all my cdrs in my dorm, so I'm kind of stuck with this breezy cd. I'll just upgrade manually after the install.

---

### Post by TheForkOfJustice on 2006-12-20
I wonder if he could install Ubuntu on a new partition and mount hda1 as his new /home directory.

---

### Post by TheForkOfJustice on 2006-12-20
> **nxn said:**
> Gparted actually failed while trying to resize it, I had to do it directly through resize2fs, hopefully my data is still ok.

And heh, yeah, I don't have a dapper or edgy cd, and I left all my cdrs in my dorm, so I'm kind of stuck with this breezy cd. I'll just upgrade manually after the install.

Get the gparted livecd from sourceforge. The gparted that comes with ubuntu tend to be a little buggy.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

(think I'll nab the new 3.3 version while I'm at it)

---

### Post by nxn on 2006-12-21
All right, I couldn't use gparted, just wouldn't work for whatever reason, and I didn't feel like driving late at night looking for a store that would sell cdr's so I could use the new gparted livecd.

Instead, I opted to shrink the partition manually using fdisk and my file system tools. Kind of scary, but at least I learned a lot. Right now everything seems fine, I didn't really thoroughly check my data yet, although quickly browsing through it everything seems as if its there. 

[http://www.justlinux.com/forum/showthread.php?t=147711](http://www.justlinux.com/forum/showthread.php?t=147711) Here's the walkthrough I used, if anyone is in a similar boat as me. Takes a little bit of math to convert between bytes and cylinders, but nothing hard really. 

So yeah, I have a /home partition now, and I can install breezy outside of it. I'm about to do this right now in fact. Thanks for the help everyone.

---

### Post by xingmu on 2006-12-23
Well, it sounds like you have everything sorted out now.  But I just want to mention a 'hack' that I used to do before.  I also had a single partition before but no way to backup my home directory. So, when I installed a new version of Ubuntu, I would move my home directory to the root filesystem as a non-standard folder name like my username 'alissah'.  In the installer, I set it to install Ubuntu to my single partition WITHOUT reformatting.  After the install was finish, my folder was still there unscathed.  Just had to move it back to the home directory.  It's not the "right" way to do it of course, but it did work for installing Breezy and Dapper.

However, it doesn't work for Edgy!  The installer seems to be different and will not mount a partition to / without reformatting it first.  So installing Edgy has finally forced me to do things right.  Now I have my own partition for my home directory.  BTW, I did that by resizing and using free space for my root partition as you did...but I didn't have the problems you seemed to have had.

---

### Post by Jamhos on 2006-12-25
I guess this is not possible, but it would be nice if there was some way you could "update" from, say... edgy to edgy, or dapper to dapper - like you would update from dapper to edgy. Then it would basically be a fresh system with any bugs erased, but important documents, programs and other packages would still be there.

Nobody knows of some sort of hack to make this possible? Maybe trick Ubuntu into thinking that it's upgrading? I would like to reinstall Ubuntu (Edgy) as I'm having a few problems, but I don't want to have to reinstall everything and set everything up again.

---

### Post by aysiu on 2006-12-25
> **Jamhos said:**
> I guess this is not possible, but it would be nice if there was some way you could "update" from, say... edgy to edgy, or dapper to dapper - like you would update from dapper to edgy. Then it would basically be a fresh system with any bugs erased, but important documents, programs and other packages would still be there.

Nobody knows of some sort of hack to make this possible? Maybe trick Ubuntu into thinking that it's upgrading? I would like to reinstall Ubuntu (Edgy) as I'm having a few problems, but I don't want to have to reinstall everything and set everything up again.
That's what having a separate /home partition is all about:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

