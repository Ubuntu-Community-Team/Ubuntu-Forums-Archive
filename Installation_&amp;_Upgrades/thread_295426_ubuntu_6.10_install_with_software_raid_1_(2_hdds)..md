---
title: "ubuntu 6.10 install with software raid 1 (2 hdds). possible swap partition?"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by cmsimike on 2006-11-08
i'm building a personal dev server and attempting to do a software raid 1. i have 2 120 gig hdds i want to use for the mirroring. i was able to tell the partioner that both drives were to be used in parts of a raid, then i was actually able to create the raid device, however i can only get it  to work with only 1 partition. i can make the entire 120 gig raid and ext 3 partition with a root mount point, however if i try to partition the raid device so taht i could have a swap partiton, it doesnt work. the second partitionn is always marked unusable. now i dont know a LOT about raids (other than that basics of what they are and how they work) so my questiona are:
is it possible to have a swap and ext3 partition on the same raid device?
if not what are my options (for instance, should i just use a 3rd, smaller hard drive for swap, or just go without swap all together?)
and if i go without swap all together, what what are the pros/cons with that? i only have 768 ram so i would like some swap space. 
anyways thanks in advance

---

### Post by cmsimike on 2006-11-08
i figured it out (i think)
each hard drive needs to be partitioned correctly (for instace 2.5 gigs for swap, rest for root)
then set up the 2 2.5 gig partitions as a raid 
and set up the other 2 partitions as a raid for root

if there's a problem with how i did this, please let me know

---

### Post by cmsimike on 2006-11-08
nevermind. when it went to boot, grub reports that it cant load the selected partition

help! :) thanks

---

### Post by wkulecz on 2006-11-08
You have to install from the alternate install cd.  Make sure your partitions are type 0xfd (software raid autodetect).  I had no troubles installing to raid1 setup as you describe.  I even added a second raid1 array later.

Problem occured when I later added a third raid5 array -- the /dev/md assignments changed and the system wouldn't boot.  I rebooted without the raid5, edited /boot/grub/menu.lst and /etc/fstab to reflect the changed md assignments, shutdown, reconnected the raid5 and rebooted.  Fine now but 6.10 is fragile when used with raid.  There is a /etc/mdadm/mdadm.conf file that is supposed to control the /dev/md assignments but it don't work!

Ubuntu raid is most definitely not ready for prime time.

--wally.

---

### Post by cmsimike on 2006-11-08
im curious why do i have to install from the alternate cd when the option for raid is on the server install?

---

### Post by wkulecz on 2006-11-08
> **cmsimike said:**
> im curious why do i have to install from the alternate cd when the option for raid is on the server install?

I guess I missed this part of your post, that you were using the server install CD.

--wally.

---

