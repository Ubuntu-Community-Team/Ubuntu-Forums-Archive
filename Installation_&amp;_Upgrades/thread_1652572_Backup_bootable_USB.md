---
title: "Backup bootable USB?"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by David_UK on 2010-12-25
I'm really chuffed with the first bootable USB stick I created so easily with 10.04 desktop.  I've added applications that I want, codecs etc and got the configuration just how I like it.

Now I'd like to back up the entire stick, as I use it a lot and the stick will die eventually.

I've not used Clonezilla, but I wondered if that would make a copy?

It's a 4G stick, with all the remaining space allocated to the casper persistance file.

Thanks

---

### Post by C.S.Cameron on 2010-12-25
Thumb drives are real easy to clone using dd.
Boot the Live CD, plug in the thumb drives and in terminal:

```
dd if=/dev/sdb of=/dev/sdc
```

Before proceeding confirm that sdb is the drive you want to clone and sdc is the target.

---

### Post by David_UK on 2010-12-25
> **C.S.Cameron said:**
> Thumb drives are real easy to clone using dd.
Great!  Thanks.  It looks as though I would be able to back it up as an image file on a DVD too.

---

