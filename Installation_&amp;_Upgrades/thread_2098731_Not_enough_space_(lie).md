---
title: "Not enough space (lie)"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by MoisesPio on 2012-12-27
Hello!

I have an Acer Aspire ONE KAV60 model, and am wanting to install Ubuntu on it.

When installing the system (after choosing the language), the installer shows that I do not have 4gb free for the installation, but I have more than 120gb.

How can I solve this?
Thanks!

---

### Post by darkod on 2012-12-27
If you already have 4 partitions on the disk, that is the maximum for msdos disks and the ubuntu installer can't create the partitions for ubuntu.

You can check all the partitions, including hidden ones, in windows Disk Management.

Post a screenshot if you need help figuring it out.

---

### Post by dino99 on 2012-12-27
instead of an automatic, you can choose a manual install 

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by MoisesPio on 2012-12-27
> **darkod said:**
> If you already have 4 partitions on the disk, that is the maximum for msdos disks and the ubuntu installer can't create the partitions for ubuntu.

You can check all the partitions, including hidden ones, in windows Disk Management.

Post a screenshot if you need help figuring it out.

You can see on [this image]("http://imgur.com/cgzqU"), i have only two partitions.

---

### Post by MoisesPio on 2013-01-15
Until now, no solution :(

---

### Post by darkod on 2013-01-15
Buy "free space" the installer is referring to unallocated space not belonging to any partition. You don't have any unallocated space since the whole hdd is used by those two partitions.

It doesn't matter how much free space (unused) you have inside C: partition, you need to have unallocated space. You have to shrink the C: partition to make unallocated space. If this is XP it doesn't have a built in tool, you have to use a third party software or Gparted from live mode on the ubuntu cd.

First only shrink C: and reboot few times. Only after XP is resized and it boot fine, start installing ubuntu. Make sure you have a full backup and know what to do if XP stops booting after the shrink, sometimes that can happen.

---

### Post by MoisesPio on 2013-01-15
So, if I format the local disk (Windows XP), the Ubuntu Installer should work, right?

I can format my local disk by Ubuntu on the live preview?

Thanks!

---

### Post by darkod on 2013-01-15
Do you want to delete XP and all data inside? If you delete it all will be lost.

---

### Post by MoisesPio on 2013-01-15
Yes, I know this!

---

### Post by darkod on 2013-01-15
In that case, it's even easier. With your ubuntu cd boot into live mode (Try Ubuntu), open terminal and execute:
```
sudo parted /dev/sda
mklabel msdos
quit
```

That will write new blank msdos table on the /dev/sda disk. After that start the install and it should go fine.

---

### Post by MoisesPio on 2013-01-15
Oh nice. I'll try ;)

---

### Post by MoisesPio on 2013-01-15
Ok, a strange thing happened.
When I run your command, my USB drive (with Ubuntu) was formatted.

I noticed that the live preview does not recognize my HD.
I'm tired and almost giving up :(

Thank you anyway my friend.

---

