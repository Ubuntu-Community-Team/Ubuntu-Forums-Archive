---
title: "Xubuntu has trouble with partitioning"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by CutterXYZ on 2007-07-28
Hello!

I get the following error message when trying to automatically partition my hard drive with the Xubuntu installation procedure: "The ext3 file system creation in partition #1 of IDE2 master (hdc) failed."

I'm trying to install Xubuntu on the whole hard-drive, so I selected the "Guided mode - Use entire disk" option at the "Prepare disk space" installation step. I clicked Next and the following summary appeared:
> The partition tables of the following devices are changed:
 IDE2 master (hdc)

The following partitions are going to be formatted:
 partition #1 of IDE2 master (hdc) as ext3
 partition #5 of IDE2 master (hdc) as swap
I clicked Next and it starts "installing the system". A window opens up showing the folders of my previous Liux system, the installation stops and an error message appears: "The ext3 file system creation in partition #1 of IDE2 master (hdc) failed."

I think the problem is that the partition of my previous Linux system has to be formated but can't be unmounted. When I try to unmount this partition with GPartEd (right click > unmount), it briefly disappears from the desktop but reappears immediately. When the automatic partitioning tool (from the Installation procedure) tries to unmount this partition so as to format it, it is probably automatically re-mounted aswell. Please tell me how to disable this partition from mounting automatically.

Thanks in advance.

---

### Post by Pumalite on 2007-07-28
Use Gparted, bootable, Live CD:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Here is a nice thread on partitioning:

[http://ubuntuforums.org/showthread.php?t=480484](http://ubuntuforums.org/showthread.php?t=480484)

---

### Post by goatflyer on 2007-07-28
Since you plan on wiping out the hard drive anyway, Try booting a LiveCD (ubuntu, knoppix, puppy, it doesn't matter) dropping into a command shell and use fdisk to delete each partition one  by one until there are no more.  Then just reboot with the xubuntu install cd and start over.  You should then see only references to partition 1 and 2.

The reason to use some Live CD is so that your hard drives are never mounted in the first place.  It is important to use fdisk on unmounted volumes only.

To use fdisk, since your drive seems to be called 'hdc', type
```

fdisk /dev/hdc

```

then use the 'l' command (lower case L) to see the list of partitions, then 'd' command to delete a specific partition number each time.  When you are done, use the 'w' command to save the new (ermpty) partition table and exit.  

Note that any old information stored on the hard disk is now basically unaccessible (gone).  There is no need to format anything now, the xubuntu installer will take care of that step.

---

### Post by [meeek] on 2007-08-19
i am having the same issue, only i am trying to wipe Windows XP and leave only Xubuntu.  I do the "fdisk /dev/hdc" command, but from there i am not sure where to proceed.

should i try formatting it to something other than ext3?

cheers
michael

---

