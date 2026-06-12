---
title: "Resizing Windows NTFS partition from Ubuntu Live USB"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by jedimattk on 2012-06-26
I've been trying out the Windows 8 release preview, and it failed to boot today with all my files trapped in its sinister arms. (I know, I ought to have backed up more recently, but my external hard drive is out of commission at the moment.) So I made a quick live USB and booted into Ubuntu, thinking I could shrink my Windows partition, install Ubuntu to a third partition, copy files over to that partition, then destroy Windows.

I opened gParted and knew there was a problem. It was unable to show how much was space was used or free on my NTFS partition, and had an exclamation mark. I *think *this means the partition has bad sectors in it.

Anyway, I got it to mount using "mount -t ntfs-3g /dev/sda2 /media/disk -o force". Once the partition was mounted, it showed up just fine in Parted, but I couldn't resize it - because it was mounted - and as soon as I unmounted it, I was back at square one. (Oh, Ubuntu, how I've missed thee.) I also tried the fix described [here]("http://www.unfinishedteleporter.com/?p=3238"), but it didn't seem to work.

It wouldn't be the absolute end of the world to lose this partition (my *really *important stuff is in Dropbox), but I have several hundred gigabytes of music, video, and pictures I want to keep around for a while. I know there's a way to do this. What am I doing wrong?

---

### Post by jmore9 on 2012-06-26
Maybe you could try gparted live cd.  Just download it and burn to cd.  Then boot off that cd. Thats pretty much all i use now a days.  It does NTFS and fat32 and all Ext's.

---

### Post by oldfred on 2012-06-26
Ubuntu's NTFS driver does not mount NTFS partitions that need chkdsk to prevent further damage that chkdsk may not then fix. If NTFS partition was resized the first thing Windows does is a chkdsk to update the new size in the NTFS partition's boot sector.

From Windows run chkdsk on the NTFS partition(s).

Also:
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

