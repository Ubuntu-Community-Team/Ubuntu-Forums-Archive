---
title: "Resize Hard Drive"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by woosingwoo on 2012-04-21
Hi,

Just new to ubuntu and need help to resize the "/dev/sda5" to make use of the unallocated free space (see below Gparted screenshot)[IMG]http://acsvideotron.brinkster.net/GParted.png[/IMG]. 



Any suggestions?
 
Thanks!

---

### Post by oldfred on 2012-04-21
Welcome to the forums.

Your link did not work for me.

If you png is a screenshot and small size, you can easily upload it as part of your message. You can use the paperclip icon in the edit panel in you new message or if editing an old one click on advanced to get full edit menu.

---

### Post by woosingwoo on 2012-04-21
any suggestions?

---

### Post by oldfred on 2012-04-21
You need to expand the extended partition into all of the unallocated. You then can move the swap all the way to the end or delete & recreate. But if you delete it you will have to update fstab with the new UUID. Then you can expand sda5.

Since it is all in the extended partition, you will have to use gparted from the Ubuntu liveCD or a gparted liveCD and click on swap and right click swap off.

Another suggestion is to leave sda5 as it is. Expand extended partition but move /home into a new partition you create in the unallocated.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by woosingwoo on 2012-04-21
Yes oldfred, thanks for your help.

Actually "to expand the extended partition into all of the unallocated" is exactly what I would like to do. Would you mind let me know how to do it?

The extended partition of /dev/sda3 can only be shrink but not extended.  :-(
Same as the ext4 of /dev/sda5, it can only be shrink but not extended as well.

---

### Post by oldfred on 2012-04-21
You should be able to expand sda3 the extended, but you have to do that first. And you have to swap-off. Then no partitions should show the little keys that prevent changes.

---

### Post by woosingwoo on 2012-04-21
yes, the little lock is next to the /dev/sda3. Tried to right click on it but only "Mange Flags" and "Information" available. Please let me know how to unlock it?

Thanks.

---

### Post by oldfred on 2012-04-21
You are using liveCD? and you have to click on swap and swapoff. LiveCD's normally mount swap if found to speed things up.

Any partition in the extended that is mounted mounts the extended also.

---

### Post by woosingwoo on 2012-04-22
yes, run GParted from LiveCD.

Swapon and Swap off can only apply to the swap partition (/dev/sda6), unfortunately, the little key on /dev/sda3 does not disappear. :-(

Please help!

---

### Post by woosingwoo on 2012-04-22
OK, now the little key is disappeared in the /dev/sda3, how can i expend the /dev/sda3 to make use of the space in /dev/sda4? see attached screenshot.

Thanks.

---

### Post by oldfred on 2012-04-22
You have repartitioned with primary partitions outside the extended. Now it is more difficult. What do you want to change?

Your sda4 is now swap and is primary. You do not show any significant unallocated. With partitions boundries set on MB you often show a small amount of unallocated to make sure drive starts on rounded sectors of optimal use. More important for new 4K and SSD drives.

---

