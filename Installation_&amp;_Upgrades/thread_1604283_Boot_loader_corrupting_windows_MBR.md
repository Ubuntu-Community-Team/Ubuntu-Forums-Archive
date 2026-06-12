---
title: "Boot loader corrupting windows MBR"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by David802 on 2010-10-23
Hey guys, so I installed Ubuntu 10.10 64 on a Compaq CQ60 laptop on a 60 gig partition with a 3 gig swap partition. I'm running windows 7 64bit ultimate on the main partition. I installed off a live disc and Ubuntu works and runs great(except for wifi >.<). 

My problem is ever since I installed Ubuntu Windows wont load every time. About half the time I select Windows 7 in the boot loader and it pulls up the windows screen with the stupid little flag, and then resets itself. 

There where no problems with Windows 7 prior to the install. I've read that if you didn't reset your computer after shrinking your drive in windows it will cause problems later. But I did that so I cant think of any other explanation for why it would continually crash. Has anybody else had this issue, is this something that might be repaired by removing Ubuntu and the partition and reinstalling it? 

Thanks for the help =P 

David M

---

### Post by richf on 2010-10-23
Try checking out this post:

[http://ubuntuforums.org/showthread.php?p=9936977#post9936977](http://ubuntuforums.org/showthread.php?p=9936977#post9936977)

I used EasyBCD to setup the dual-boot w/Win 7. Works great & free!

---

### Post by srs5694 on 2010-10-24
It sounds to me like the Windows drive is not being properly unmounted. Are you shutting down Linux properly, or just turning off the computer? If the latter, ***don't!*** Linux caches all disk accesses, which means that data structures on the disk are not in a consistent state until the disk is unmounted. This can be done manually or when you select the system shutdown option.

If you *are* shutting down, it's conceivable that something is interfering with unmounting the Windows partition. I've seen this happen once or twice with NTFS, but I've never investigated the cause. You could try closing all the files you have open on NTFS and unmounting manually before you shut down. If you don't normally need to access the Windows partition, you can keep GNOME from mounting it by creating an entry in /etc/fstab, something like this:

```

/dev/sda2  /mnt/windows  ntfs-3g  noauto,users  0 0

```

Change /dev/sda2 to the device file for your Windows partition, or change it to use a suitable UUID= or LABEL= reference. You'll need to create the /mnt/windows mount point; or you can change it to something else. With this in place, the system won't mount the Windows partition unless you explicitly tell it to do so by typing "mount /mnt/windows" (or whatever mount point you choose).

---

### Post by oldfred on 2010-10-24
Are you hibernating windows and then writing data from Ubuntu into the windows system partition? That will definitely cause problems. Is windows wanting to run chkdsk?

If your windows booted after install then the issue is not related to the resize for the install.

---

### Post by jtarin on 2010-10-24
> **richf said:**
> Try checking out this post:

[http://ubuntuforums.org/showthread.php?p=9936977#post9936977](http://ubuntuforums.org/showthread.php?p=9936977#post9936977)

I used EasyBCD to setup the dual-boot w/Win 7. Works great & free!I highly recommend for a dual boot setup. (see my signature)

---

