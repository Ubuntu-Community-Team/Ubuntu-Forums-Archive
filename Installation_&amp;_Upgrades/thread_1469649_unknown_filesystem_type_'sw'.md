---
title: "unknown filesystem type 'sw'"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by mistaken on 2010-05-02
upgraded to 10.04 and now cannot login...
they say, that  could not mount swap. let me do it manually, or skip. Manually, tried to edit /etc/fstab, but not workin...
i see error when loading:
unknown filesystem type 'sw'
filesystem could not be mounted : swap
mount swap [757]terminated with status 32


what should I do?
I have lots of partition, two addintional for swap, like /dev/sda7 and /dev/sda10. they were left on fstab after upgrade, but nor working... 

how can i get i into ubuntu?? install a new version? :(

---

### Post by srs5694 on 2010-05-02
Check your swap entries in /etc/fstab. Here's an example from one of my systems:

```

UUID=9c71c5a7-97bd-45fd-b9a5-b377ee636972 none  swap  sw   0  0

```

If that "swap" is "sw", change it to "swap". If the second column ("none" here) is missing, add it. If anything else is different, other than the UUID value, then change it to match the above. Also, at least one of my systems uses "swap" rather than "sw" in the fourth field, so if everything matches my example, you could try changing "sw" to "swap", although since "sw" clearly works on most of my systems, I'd be puzzled by the need to change it, unless maybe "sw" as an option has been deprecated and I haven't heard of it yet.

If all else fails, you can try commenting out the swap line(s) from your /etc/fstab by placing has marks (#) at the start of each line. That'll at least get the system booting normally, whereupon you can investigate and experiment further.

---

### Post by mistaken on 2010-05-04
thanks for an answer.
my /etc/fstab was perfect all the time - I was using it for three months and haven't changed anything and it was the same as you mentioned, just instead of uuid was /dev/hda8. And everything failed just after upgrade... but whatever, I already tried to install xubuntu 10.04. Unfortunately, it did not wanted to work, so i installed 9.10 and now everything is fine. Maybe one day I'll try upgrade again...

---

### Post by srs5694 on 2010-05-04
Chances are your upgrade changed the device number, so /dev/sda8 no longer referred to your swap partition. You can either change the device number to whatever was appropriate (typing "sudo fdisk -l" will list your partitions; search for one that's marked as being Linux swap) or change /dev/sda8 to a UUID= entry (type "sudo blkid" to list all your partitions' UUIDs, and search for the UUID for your swap partition).

---

