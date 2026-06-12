---
title: "Won't Mount vfat"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by LeeM on 2012-02-24
Hi!

I'm baffled. Just loaded 11.10 (after blowing away 11.10 by mistake!. I installed 11.10 with Gnome3 (from Linux Format DVD). When I try to mount a USB stick, I got an error message "Error mounting mount: unknown filesystem type 'vfat'". WHOA! Never seen that before. Any idea where to look?

TIA.

---

### Post by roelforg on 2012-02-24
```

sudo apt-get update
sudo apt-get install dosfstools

```

---

### Post by LeeM on 2012-02-24
> **roelforg said:**
> ```

sudo apt-get update
sudo apt-get install dosfstools

```

Did that.  It says dosfstools is already the newest version. 
I get same error message as previous when trying to mount thumbdrive.

---

### Post by hairyharry7 on 2012-03-31
EXACT same thing happens to me...

i have a shared partition on a dual boot that is formatted as fat32. on start up it says it can't mount the shared drive and i have to say to skip it. once i log in i try to mount the drive using gparted and i get the same error message. anybody have any ideas about this???

thanks

---

