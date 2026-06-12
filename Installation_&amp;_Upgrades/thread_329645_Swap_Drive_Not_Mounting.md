---
title: "Swap Drive Not Mounting"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by thrillhouse on 2007-01-01
I just noticed that when I upgraded to edgy that my swap drive isnt mounted anymore.  I can do a 'mkswap' and then 'swapon -a' and its ok but then it isnt mounted on restarts.  Any ideas?  If you need more info, just let me know where i need to get it.

---

### Post by chippy99 on 2007-01-01
Have a look at the file /etc/fstab It should have a line something like 

/dev/hda2               none            swap            sw              0 0

If it doesn't you will need to add it changing the device name to whatever your swap partition is.

---

### Post by thrillhouse on 2007-01-10
Thats what I have in my fstab.  The swap doesnt mount when I hibernate and unhibernate it.  Not to mention that it doesn't restore where it should when I wake the computer up, but I suspect that has something to do with not mounting the swap.

---

### Post by chippy99 on 2007-01-12
Have a look at this post [http://ubuntuforums.org/showthread.php?p=1683612](http://ubuntuforums.org/showthread.php?p=1683612)

---

