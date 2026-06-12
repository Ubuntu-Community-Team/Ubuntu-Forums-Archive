---
title: "[SOLVED] Help, GRUB reinstall, Partition help needed"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by longlivethebestos on 2008-11-26
I have a pc with a dual boot config, First I had Vista then I installed Ubuntu 8.10 everything was fine until I deleted an extra partition. I restarted only to find that Grub was corrupted..... Anyway I found this site: [http://www.techrecipes.net/linux/recover-lost-corrupted-grub-mbr.html](http://www.techrecipes.net/linux/recover-lost-corrupted-grub-mbr.html) 

On there it tells me what to do exactly, but I have a problem, the instructions talk as if the user has 1 partition, I have 6;

/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda5
/dev/sda6 - ubuntu installation
/dev/sda7

I did what it said and mounted 'sda6'. Everything was fine until it said:

''Assuming Linux is installed in the first partition of the first harddisk, run the following actions would restore the MBR. If the the installation is done at some other partition or harddisk, change the (hd0,0) and (hd0) accordingly.''

Now I don't know what my sda6 is and I don't want to guess. So here I am running off the live CD, can anyone help me with the info that I've provided?

Help would be appreciated!!

Thanks

---

### Post by unutbu on 2008-11-26
To reinstall GRUB, try Catlett's instructions:
[http://ubuntuforums.org/showpost.php?p=1308395&postcount=1](http://ubuntuforums.org/showpost.php?p=1308395&postcount=1)

This might also help:
```
Linux device name           GRUB name
/dev/sda     		    (hd0)
/dev/sda1                   (hd0,0)
/dev/sda2		    (hd0,1)
...
/dev/sda6		    (hd0,5)

/dev/sdb		    (hd1)
/dev/sdb1		    (hd1,0)
```

---

### Post by caljohnsmith on 2008-11-26
How about doing the following from your Live CD:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Please post the output of the above commands, reboot, and let me know what happens. :)

---

### Post by Coreigh on 2008-11-26
Posting the out put of ```
sudo fdisk -l
```will help determine the correct values for (hd0,0) and (hd0). 

You listed partitions 1,2 ,3, 5, 6, & 7. I assume you deleted 4, BUT did you empty the partition and leave it blank? or did you resize #3 or #5 to take up the space? These answers will affect the partition order and numbering.

---

### Post by longlivethebestos on 2008-11-26
Thanks to all, It worked (Well it says sucessful) So thanks.

Those other instructions are too advanced (And basically rubish)

Thanks soo much again.

I'll post back after reboot!!

Fingers crossed!!

Thanks

---

### Post by longlivethebestos on 2008-11-26
It works, Just like it did.

Phew - All my data is still there

Thanks for the last time!

---

