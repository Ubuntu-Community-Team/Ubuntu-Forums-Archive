---
title: "os not found"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by qiemem on 2008-03-01
I just installed Ubuntu on a laptop that a friend is letting me borrow.  However, whenever I try to boot from the hard drive, it will go through a ram test and stuff like that, but then grub will not load and it stops with "Operating system not found".

I've installed Linux on this computer before (I think it was Linux Mint) and I don't think I had much trouble.  After that, my friend reinstalled XP, had some trouble with getting it to boot, but doesn't now remember what he had to do to get it to work.  I'm not dual-booting or anything like that.  

I've tried reinstalling several times with various partition set ups, but nothing seems to help.  Livecd boots up fine every time and I can see all of the files on the hard drive.

I'm afraid I don't know anything about the hardware inside.  I can't find a brand name or anything on it; it seems to be some sort of custom deal.  It only says "Notebook" on the top.  Kinda weird...  It is also the largest laptop I have ever seen.  There is supposed to be two hard drives in there, but one is apparently broken.

Oh, last thing.  I tried using Super Grub Disk in case grub had gotten messed up in anyway/to locate grub manually.  However, it was unable to even find grub.

Any ideas?  I would really appreciate any help; I need this laptop for school as mine just died...

---

### Post by dstew on 2008-03-01
Boot the Live CD, open the Terminal application and enter on the command line```
sudo fdisk -l
```Post the result to the forum.

---

### Post by qiemem on 2008-03-01
```

$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x736912ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

```

---

### Post by confused57 on 2008-03-01
If you haven't already, have you tried a direct kernel boot using Super Grub Disk?

---

### Post by qiemem on 2008-03-01
I think so.  It says file not found, though, I think referring to some grub files. 

Also, I should note that after the RAM test, I get a flashing message saying array not found, or something like that...

---

### Post by qiemem on 2008-03-02
The message was actually "No arrays defined".  It gave me the option to configure things, so I did, and sorta just poked around until I was able to create an array of the whole hard drive. Now it works great!  Thanks for trying to help!

---

