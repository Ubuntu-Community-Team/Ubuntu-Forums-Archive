---
title: "I shouldn't have done it...  :o)"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by Xswitch on 2011-07-01
Hi Everybody...  I upgraded my sweet running ubuntu 10, and am now regretting every minute of it...  So I have some questions...

1. Is there like a restore button that will put your system back to the way it was before you screwed it up? :p  ...  Something like an **_"undo" upgrade button_** would be nice...  :lolflag:

2. After doing some reading on how to fix my problem, I found this: 

> **unutbu said:**
> ruru, if you save your /etc/apt directory to a USB flash drive, then do a fresh install, then copy the /etc/apt directory from the flash drive to the root partition of the fresh install, then you should be good to go.

Edit: You may need to open a terminal (Applications>Accessories>Terminal) and run
```

sudo apt-get update
```
to make the fresh install aware of the packages available).


**I upgraded from 10.x to 11.04.  Can I do this and not have to install ALL of my apps manually?  Can I just reinstall 10.x, copy the above dir to the fresh 10.x install and be ok?**

Thanks all...

---

### Post by dino99 on 2011-07-01
something is not clear : you never have to reinstall your apps if you have a separate /home where your apps config & settings are & all the private data

but there is no "undo" in real world :)

what is wrong with your upgrade ? Look & feel ?

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by akand074 on 2011-07-01
You can't revert an upgrade. I believe you'll have to do a clean install. 11.04 not running well? As in the upgrade caused some breakage?

---

### Post by Xswitch on 2011-07-01
> **dino99 said:**
> something is not clear : you never have to reinstall your apps if you have a separate /home where your apps config & settings are & all the private data

but there is no "undo" in real world :)

what is wrong with your upgrade ? Look & feel ?

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Thanks dino99...  Here's my HDD setup:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              83G  4.4G   74G   6% /
none                  4.0G  732K  4.0G   1% /dev
none                  4.0G  2.7M  4.0G   1% /dev/shm
none                  4.0G   92K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
/dev/sdb1             459G   45G  391G  11% /home

The entire **sdb1** is designated as my /home.  Based on this info, can I just reinstall 10.10 on sda2?  Should be ok right?  

Don't like 11.04 at this point...  I'll install in a vm and play, (which is what I should have done in the 1st fat place... :lolflag: )

Also, I think last time I installed **32bit**.  Should I install **64bit**, or leave that alone...  I heard 64bit was problematic...

Thanks akand074...  I think I just need to work with it in a separate environment first...  not on my main system...

---

### Post by Xswitch on 2011-07-03
Reinstalled 10.10...  added line to fstab /dev/sdb1    /home    ext4

Some apps did not show or run correctly...  Just reinstalled them and all is now well with my world...  :)

---

### Post by Sef on 2011-07-03
> You can't revert an upgrade. I believe you'll have to do a clean install. 

That is correct.

---

