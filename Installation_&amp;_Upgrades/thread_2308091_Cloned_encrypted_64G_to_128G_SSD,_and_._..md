---
title: "Cloned encrypted 64G to 128G SSD, and . ."
date: 2015-12-30
forum: Installation &amp; Upgrades
---

### Post by wjbmd48 on 2015-12-30
Hi All:

I'm running full disk encrypted Lubuntu 14.04 LTS on a 64G SSD (Kingspec 1.8" IDE PATA on an Thinkpad).

I went to clone it, using clonezilla to a 128G SSD using Expert mode with the -r option (attempt to resize).

It didn't; the target disk now runs the encrypted install well, but only shows at 64G with df -h.

In the Disk Utility, it shows as 127G, but there are 2 Block Drives, 62G and 1.6G.

Is there a way to enlarge the primary partition from 62-64 G to the full 128G?

Thanks!

Bill

---

### Post by ubfan1 on 2015-12-30
Did you look at resize2fs ?  Don't know if that would work on an encrypted fs though.

---

### Post by oldfred on 2015-12-31
If full disk encryption, then it is LVM, which I do not know.
But believe you have a multiple step resize. First you have to resize the physical partitions, then resize the logical partitions with LVM tools.

       [http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

### Post by wjbmd48 on 2015-12-31
I did, thanks, and, no, you're right, won't work with an encrypted setup.

I guess it doesn't make sense that you can resize an unmounted encrypted partition.

What I don't get, tho, is that when I look at the unmounted partition with Gparted, I see that:

sdb1 485 Mb  OK, that's the boot
sdb2 117 GB extended
sdb5 ! 117 GB crypt-luks
4.99 Mb unallocated, i guess that's what's left over . . 

it's identified as sdb because i'm mounting it on another system with a usb harness

but when i boot to it with the password, i only see 57 GB in terminal with df -h.

I guess the problem is I don't understand the mounting system that well.

This ain't a major problem.  I've tried a clean install of the 128 GB disk, and when I do, I indeed see the full 128 GB, but, oddly, most Wine programs don't work.  I've tried this twice on different systems, same thing. Even tried booting to earlier kernels.

Annoying, but livable. More curious than anything else.

Thanks!

---

### Post by oldfred on 2015-12-31
The LVM logical partition uses the entire physical partition.
And then the logical partitions are what you mount & use in Ubuntu, so only the amount of data you have actually used in the LVM partitions is what df -h shows.

---

### Post by wjbmd48 on 2015-12-31
You guys are the best, thanks!

So, I have a lot to learn, it appears, thanks for the links.

One  basic question, if I may:  if df -h only shows the amount of data actually used  in the LVM partitions, is there an easy way to reclaim the half of the  physical volume not shown in the logical volumes seen in df -h into  those logical volumes, or into new ones?

I.e., my LVM is only using half the physical disk; is there away of reclaiming the other half into an LVM system I can see?

Thanks!

Bill

---

### Post by oldfred on 2015-12-31
Once you change to LVM, that is what you use. 
Its advantage is that you can more easily change partitions within the LVM with LVM tools. 
But the disadvantage is that you have to use LVM tools and mount and use the LVM partitions not the typical sda1 physical partitions.

---

### Post by wjbmd48 on 2016-01-01
Thanks all,  marked solved, greatly appreciated. OK, got it figured out, learned a few things as well.

I've got to say that over the years Ubuntu has gotten steadily easier to use for non-techies like me.  And I'm sure never going back to a commercial OS.  And you guys are fantastic.

Best,

Bill

---

