---
title: "Increazing partition size?"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by h4x0rmx on 2010-07-08
I'm attaching a screenshot of my partitions info on GParted under a liveUSB so that you can have an idea of what I'm talking about.
I have 5.88GB of unallocated space in my HD that I want to assign to my last partition /dev/sda6 ext4. I would combine the unallocated space with the extended partition and then resize until I get what I want, but I don't really know how to do it.
I think that my main problem is that I already have 4 primary partitions so if I want to create a new partition with the unallocated space I get a message that won't allow me to create a partition. GParted won't let me do anything on the extended partition. How else could I manage to merge the unallocated space with my ext4 partition?

---

### Post by ronparent on 2010-07-08
I think that you have to run gparted from a live cd because the affected partitions have to be unmounted.

---

### Post by h4x0rmx on 2010-07-08
> **ronparent said:**
> I think that you have to run gparted from a live cd because the affected partitions have to be unmounted.

I'm running GParted from a liveUSB so the partitions I want to resize are not mounted. :)

---

### Post by Rubi1200 on 2010-07-08
Do you see the key sign next to the extended and swap partition?

You cannot change anything until you right-click and choose Swapoff.

---

### Post by h4x0rmx on 2010-07-08
> **Rubi1200 said:**
> Do you see the key sign next to the extended and swap partition?

You cannot change anything until you right-click and choose Swapoff.

I had swappedoff, but I didn't try to right-click again to see if something had changed! :P
It seems to be working now, hopefully everything will go alright as I didn't make a backup
:oops:

---

### Post by h4x0rmx on 2010-07-08
By the way, I read that if you modify the swap partition, its UUID will be changed and you will  need to update the /etc/fstab with the new UUID.
Will I need to do this? If so, how would I do it? :)

---

### Post by Rubi1200 on 2010-07-08
GParted is a great tool for working with partitions, but you should ALWAYS backup before attempting stuff like that because you never know what might go wrong.

---

### Post by Rubi1200 on 2010-07-08
> **h4x0rmx said:**
> By the way, I read that if you modify the swap partition, its UUID will be changed and you will  need to update the /etc/fstab with the new UUID.
Will I need to do this? If so, how would I do it? :)

This should help you along the way:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by h4x0rmx on 2010-07-08
Awesome!!! Everything is working right, I know I should've made a backup.

Thanks for the help!!!

---

