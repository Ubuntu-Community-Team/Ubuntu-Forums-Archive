---
title: "Help Extending Ubuntu Partition"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by kaneone on 2013-02-16
Hi, I'm new here, so I apologize if I posted this in the wrong section.

I want to extend my "ext4" partition with an unallocated partition. Here's how my partitions look:

[IMG]http://img72.imageshack.us/img72/2900/screenshotfrom201302162.png[/IMG]

What I thought I should do is:
1. Extend the "extended" file system by 75.00 GiB. After doing that, the unallocated file system will be above the linux-swap.
2. Now I think I should delete the linux-swap, but when I do that, it moves "ext4" to "dev/sda5," which I'm not sure if that's a good idea.
3. Extend the "ext4" partition and leave 954.00 MiB.
4. Make a new linux-swap partition out of the 953.00 MiB unallocated partition.

This is my first time doing something like this, so I doubt I'm doing a good job. Before I do all that, should I do something else instead?

---

### Post by oldfred on 2013-02-16
You cannot make any more primary partitions so swap will have to be inside the extended. You can shrink the ext4 and add swap after or leave room at the front of the extended.

You may be just able to move swap left & then move sda6 left, then expand sda6 right.

If you delete swap and recreate it, it will get a new UUID and you will have to edit fstab with new UUID. Just moving partition should not change UUIDs & you should be able to boot, but sometimes you still have to reinstall grub, so make sure you know how to do that. 

You have to do all this from liveCD or flash drive and click on swap, right click swap off to unmount it.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by kaneone on 2013-02-17
Thank you, it worked!

---

