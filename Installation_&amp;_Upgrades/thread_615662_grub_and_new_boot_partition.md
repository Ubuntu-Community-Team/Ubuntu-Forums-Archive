---
title: "grub and new /boot partition"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by jsundqui on 2007-11-17
I tried to upgrade from 7.04 to 7.10 but it aborted because my /boot partition was too small. I guess I am too old school linux, and nowadays, grub doesn't have the same problems lilo had with large disks, but I still set up a separate /boot partition at the front of the disk.  

But now its 100 MB size is too small according to the 7.10 upgrader, and I can't resize it with QTparted since the / partition is sitting just after it.

I've got a swap partition on another drive that I shrank and made a new 250 MB partition for a new /boot and I have that mounted as /boot at start up (by editing /etc/fstab), but I know that grub isn't looking there for the boot files, so if I go upgrade I'll end up with a dead system.

It appears that grub looks for the partition from which to read it's set up files from the 

# groot=(hd2,0)

line in menu.lst, correct?  This would be pointing to the first (zeroth) partition on my third (gotta love starting to count from 0) hard drive, which was where my old /boot was (and still is, although not mounted).

My new /boot partition is on /dev/sdb6, also known as the second logical partition on the extended partition of my second hard drive.

My questions are thus:

(1) to get grub to look at my new /boot partition, do I edit just the "# groot=(hd2,0)" line in menu.list?  Do I *not* have to run a command like in the old days with lilo where you had to run the lilo command after editingin lilo.conf (yes, I did read the grub man page, but I am still confused)

(2) /dev/sdb6 is what in the alternate nomeclature?  i.e. if it is (hd1,X), what is "X"?  Is it "6"  I am pretty sure it isn't.  I am guessing it is "3" (with 0 being the first primary, 1 being the extended partition, 2 being the first logical and 3 being the second logical), but I'm not sure.

BTW, the "similar threads" is a great feature of this forum.  I thought I would get insight from [http://ubuntuforums.org/showthread.php?t=534985](http://ubuntuforums.org/showthread.php?t=534985) which pointed me to [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

But when I ran 

grub> find /boot/grub/stage1

I got 

Error 15: File not found

So that is not good.

Thanks.

---

### Post by zvacet on 2007-11-17
[http://users.bigpond.net.au/hermanzone/p15.htm#15]("http://users.bigpond.net.au/hermanzone/p15.htm#15")

---

### Post by meierfra on 2007-11-17
> 1) to get grub to look at my new /boot partition, do I edit just the "# groot=(hd2,0)" line in menu.list? Do I *not* have to run a command like in the old days with lilo where you had to run the lilo command after editingin lilo.conf (yes, I did read the grub man page, but I am still confused)


You also need to run

```
sudo update-grub
```

That will update your menu.lst according to  the new groot information.
(or manually change all appropriate   "root (hd?,?)"  in menu.lst to "root (hd2,0)"


> Mynew /boot partition is on /dev/sdb6, also known as the second logical partition on the extended partition of my second hard drive.

/dev/sdb6 is (hd1,5).


> 
grub> find /boot/grub/stage1


Try "find /grub/stage1" instead.

---

### Post by jsundqui on 2007-11-20
Thanks meierfra

All your points were spot on.

---

