---
title: "Removing partition?"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by dc12volthippy on 2007-05-25
I have a partition that I have to remove. How do I do this?

---

### Post by taurus on 2007-05-25
Use gparted from System -> Administration.  And if you don't have one, install it.

```
sudo aptitude update
sudo aptitude install gparted
```

---

### Post by dc12volthippy on 2007-05-25
I tried, but it won't work, it has an error when I try to make the partition as small as it goes.

---

### Post by MattParkins on 2007-05-26
Follow up question, similar to this one.  

I'm in the process of migrating from XP to ubuntu and I'm very nearly there.  I have installed ubuntu on my 2nd partition with XP on the first.  Once I've completed the migration and am ready to remove the XP partition is it possible to delete the XP partition and move ubuntu partition to take up the entire drive?  Or should I just format it and use it as a storage area - I know that would be easier, but I like just having one drive?

I think I'm being a bit hopeful and it'll need a full reinstall, but at least I'll know where everything is...  

Thanks in advance :)

---

### Post by merlinus on 2007-05-26
In response to dc12volthippy:

It sounds like you are trying to re-size the partition.  Didn't you want to delete it?

It will then free up the space, which you can add to other partitions or for something else.

Also, youc annot re-size or delete a mounted partition -- it has to be unmounted first.

I would also recommend downloading gparted live cd and burn it as a disk image.  You can then boot from it and do anything with your partitions, because they will be unmounted.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Good luck!

-merlin

---

### Post by merlinus on 2007-05-26
> **MattParkins said:**
> Follow up question, similar to this one.  

I'm in the process of migrating from XP to ubuntu and I'm very nearly there.  I have installed ubuntu on my 2nd partition with XP on the first.  Once I've completed the migration and am ready to remove the XP partition is it possible to delete the XP partition and move ubuntu partition to take up the entire drive?  Or should I just format it and use it as a storage area - I know that would be easier, but I like just having one drive?

I think I'm being a bit hopeful and it'll need a full reinstall, but at least I'll know where everything is...  

Thanks in advance :)

You can start over and tell the live cd partitioner to use the entire disk, or re-format the xp partition afterwards as ext3 and mount it as /home.

In that case you may have to edit /etc/fstab and perhaps a few other configuration files.

-merlin

---

### Post by dc12volthippy on 2007-05-26
Ah, screw it! I'm just gonna use the Kubuntu CD and select "Uninstall" in the main menu thingy.

---

