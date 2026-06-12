---
title: "usb installation, which syntax is right ?"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by Paleskin on 2012-09-08
I installed ubuntu, as full install into usb flash drive

In order to longer my flash drive lifetime, and to increase performance, these are what I already did :

> tune2fs -o journal_data_writeback /dev/sda1

> tune2fs -O ^has_journal /dev/sda1

> e2fsck -f /dev/sda1

And I verify that the journaling feature is turned off by 

> debugfs -R features /dev/sda1

And the last step was to put the line **data=writeback,noatime,nodiratime **in fstab using

> gksu gedit /media/sda1/etc/fstab

This is where I got confused, which one is right among these ?


> UUID=fd2dba10-a6b3-4e9c-84e7-ec427ea66f6a / ext4 data=writeback,noatime,nodiratime errors=remount-ro 0 1

> UUID=fd2dba10-a6b3-4e9c-84e7-ec427ea66f6a / ext4 data=writeback,noatime,nodiratime,errors=remount-ro 0 1

> UUID=fd2dba10-a6b3-4e9c-84e7-ec427ea66f6a /               ext4 errors=remount-ro,data=writeback,noatime,nodiratime 0       1

Also, the spaces between text sometimes longer, sometimes shorter, is there any differences between longer and shorter ones ? do they affect anything ?


Thanks

---

### Post by darkod on 2012-09-08
The space length doesn't matter. Also, make sure all options are separated only by comma and there is no space between them. And leave the default errors=remount-ro in there.

So, according to this, the second option looks correct. There should be space before 'data' and after the 'remount-ro', no other spaces between the options. Just one comma between each.

---

### Post by Paleskin on 2012-09-09
> **darkod said:**
> The space length doesn't matter. Also, make sure all options are separated only by comma and there is no space between them. And leave the default errors=remount-ro in there.

So, according to this, the second option looks correct. There should be space before 'data' and after the 'remount-ro', no other spaces between the options. Just one comma between each.

What are the last 0 1 numbers represent ?

---

### Post by darkod on 2012-09-09
> **Paleskin said:**
> What are the last 0 1 numbers represent ?

Not sure about that. The root partition usually has the 0 1.

---

