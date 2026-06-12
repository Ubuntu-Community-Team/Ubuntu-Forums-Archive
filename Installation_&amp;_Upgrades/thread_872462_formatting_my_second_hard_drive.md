---
title: "formatting my second hard drive?"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by wsamh on 2008-07-28
I want to format my second hard drive with ext3, but I get a prompt that says that I don't have permission. How can I fix that?

---

### Post by iaculallad on 2008-07-28
> **wsamh said:**
> I want to format my second hard drive with ext3, but I get a prompt that says that I don't have permission. How can I fix that?

You could use the Gparted utility or on the terminal:

```
sudo mkfs.ext3 /dev/the_partition_you_want_formated
```

---

### Post by Rocket2DMn on 2008-07-28
Alternatively you can install GParted
```
sudo apt-get install gparted
```
Then access it from System->Administration->Partition Editor.  You will need to make sure the drive's partition(s) is/are unmounted, then you can delete the existing partitions on that secondary device and reformat it with ext3.  Assuming this drive is internal, you will want to add or edit a pre-existing fstab entry for this device, which I can help you do after you format it.

---

### Post by Sef on 2008-07-28
Or you can download [GParted]("http://gparted.sourceforge.net/") itself.

---

