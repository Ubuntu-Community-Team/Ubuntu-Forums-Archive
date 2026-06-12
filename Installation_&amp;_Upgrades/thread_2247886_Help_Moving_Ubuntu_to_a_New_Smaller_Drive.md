---
title: "Help Moving Ubuntu to a New Smaller Drive"
date: 2014-10-11
forum: Installation &amp; Upgrades
---

### Post by scmaruthi on 2014-10-11
This problem would be very simple if I had an additional large drive but I don't.

I have a Ubuntu 14.04 Server installed on a 250GB HDD.
There are a lot of files stored in my home folder and certain other directories.
I would like to move the OS to a new 64 GB SSD.
I don't have an extra HDD to make a backup.

I would like to copy the exact Ubuntu Install except for certain folders.
Is that possible ?
After the shift, I could remount the old folders back to their same locations
and the dependent programs wouldn't have a problem.

Something like

>clone /dev/sda to /dev/sdb --except /home/data/ ... ... ... /something/else/

I'm not too well versed in Linux.
So please try to be simple.

Thanks.

---

### Post by ecophobia on 2014-10-11
You can use **GParted**  to shrink down the partition(s) and clone it  over to you smaller drive by using either dd or **Clonezilla**

As an alternative, take a look at Acronis. I haven't used it for a wile, but I remember cloning Lin OS onto a smaller drive with no probs. Get the trial to see for yourself.

---

### Post by scmaruthi on 2014-10-11
Although Acronis says that it can handle Linux Partitions, I'm not able to find any of its consumer software that runs on Linux.

I would like to skip any partitioning operations on my 250GB HDD.
I understand that with GParted I could create a partition on the free space and move my files and keep resizing the new partition and moving additional files until the OS Partition is small enough. But I don't want to risk any of my data or spend time recoverying them later on.

Is there a way to migrate a whole partition skipping just the folders I mention that I don't want to be moved ?

---

### Post by ecophobia on 2014-10-11
Acronis is Windows soft, but can clone Linux etc. It can also work as a boot CD and can restore OS to different hardware (incl smaller HHD)
You have partitions and boot record on your hard drive. These are allocated places and locations on you hdd. 
When you clone, you transfer all the information regarding hdd geometry to another disk.
If it is different, you need to change these records, which is not particularly difficult to do in hex editor for an experienced (read geek) IT person. 
I would back up you precious files and try resizing and cloning. 

Alternatively, just install Unbuntu on you new hdd and only migrate your home directory to the new drive.

"When restoring a disk, **Clonezilla enables you to resize the filesystem  and create partitions on the new disk proportionally.** But even if you  are moving to a bigger disk, you might prefer to keep the partitions as  they are. In that case you can ask Clonezilla to create the partition  table as its listed in the image."

Try Clonzilla, it looks like it can resize partitions when you copy them onto another drive. This should leave your original drive intact and you can experiment with Clonezilla and your new - smaller drive.

---

### Post by sudodus on 2014-10-11
> **scmaruthi said:**
> This problem would be very simple if I had an additional large drive but I don't.

I have a Ubuntu 14.04 Server installed on a 250GB HDD.
There are a lot of files stored in my home folder and certain other directories.
I would like to move the OS to a new 64 GB SSD.
I don't have an extra HDD to make a backup.

I would like to copy the exact Ubuntu Install except for certain folders.
Is that possible ?

Yes, it is possible, but I think more difficult and risky than to make a fresh install and tweak it to do what you want.
> 
After the shift, I could remount the old folders back to their same locations
and the dependent programs wouldn't have a problem.

Something like

>clone /dev/sda to /dev/sdb --except /home/data/ ... ... ... /something/else/

I'm not too well versed in Linux.
So please try to be simple.

Thanks.

Possible method:

1. You can create the partitions that you want in the SSD with ***gparted***.

2. Copy the directory tree with ***rsync***. The manual ```
man rsync
``` describes how to exclude files and directories.

3. Install the ***bootloader*** into the head of the SSD

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

-o-

But often it is more efficient to make a fresh install, because you can get unexpected problems when you transfer parts of a system.

---

### Post by scmaruthi on 2014-10-24
Thanks for your suggestions guys.
@sudodus
I could have used your suggestion of rsync. It seems more easy than copying each one individually.
But I did not check your reply at that time.

I finally got it done.
Firstly, the reason I did not want a fresh install is that being new to Linux, I've spent a lot of time customizing my setup.
I just could get myself to reinstall and redo all the tweaks.  
I did not want to partition because I did not have a third drive to backup and was worried for the same above reason.
No matter how good the software is and non destructive its functioning is, it feels like a risk to do anything on the drive.

The Solution (which worked for me)
I found a guide @ [http://blog.oaktreepeak.com/2012/03/move_your_linux_installation_t.html](http://blog.oaktreepeak.com/2012/03/move_your_linux_installation_t.html)

I followed almost the whole guide, with the exception of the line which transfers all the files in one go.
```
[COLOR=#333333]sudo cp -afv /mnt/old_drive_boot/. /mnt/new_drive_boot[/COLOR]
```[COLOR=#333333]
[/COLOR]
Instead I manually copied all linux OS files/folders while skipping the folders in the home directory that I did not want to carry over.

For anyone else trying it out, know the distinction between your folder and the ones the OS is dependent on.

After finishing, I remounted the old folders (which I did not copy to the new disk) back to their same locations on the directory tree.

All the stuff now works :D
Even if something were to go wrong half way through, I would still be able to boot from the orignal HDD.
Thanks..

---

