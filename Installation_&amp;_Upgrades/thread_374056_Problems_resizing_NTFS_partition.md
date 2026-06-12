---
title: "Problems resizing NTFS partition"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by aosmith on 2007-03-02
Hi,
I have installed ubuntu (as well as fedora gentoo etc etc.) but now im trying to setup a dual boot on my win xp machine.  I can't seem to resize the xp partition (NTFS) using gparted boot disc or the ubuntu install/live dvd (i think it uses gparted aswell).  I defraged right before but still no dice.  I was trying to avoid using a ghosting utility but im quickly running out of options... An a fresh install of xp is just not an option (I've have bad experiences with thinkpad r&r and extra partitions)... Any ideas? other utils etc?
Thanks
-Alex

---

### Post by taurus on 2007-03-02
Maybe the latest version of GParted LiveCD works better.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by mikewhatever on 2007-03-02
> **aosmith said:**
> I can't seem to resize the xp partition (NTFS) using gparted boot disc or the ubuntu install/live dvd (i think it uses gparted aswell). 
-Alex
Can you clarify that sentence please. Is there an error message? What happens exactly? How do you know you can't resize the XP partition?

---

### Post by warjowuch on 2007-03-02
That would indeed be usefull, we are waiting to help!

---

### Post by aosmith on 2007-03-02
Well in the time span that my internet was down last night i figured it out... just for everyone out there i had to compress my drive then defrag and install went through without a hitch

---

### Post by orb9220 on 2007-03-02
No you did not have to compress just defrag. In fact I don't know if ntfg3 allows you to access a compressed ntfs partition.

This is what happened to me before I ran defrag a couple of times and all was well.

---

