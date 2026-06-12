---
title: "How to delete ubuntu"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by th081 on 2011-08-28
Hello,

I have a laptop dual booting windows 7 and Ubuntu. The hard drive of the laptop has three partitions, Windows, Ubuntu (working) and Ubuntu (that does not work). 

What i want to do is delete the two partitions with Ubuntu create one big one then reinstall Ubuntu. I don't have the original windows disk as it was preinstalled, i have created a recovery disk but it does not give the option to delete the ubuntu partitions /reinstall windows. Windows is working fine, could i format the two ubuntu partitions through windows then reinstall ubuntu. Would that cause an issue with the loader that appears at the start.

ideally i want to delete the loader so that it boots straight into windows then delete and reinstall ubuntu.

thanks for any help

---

### Post by dino99 on 2011-08-28
follow this howto for installing, burn partedmagic on cd or use a usb-stick, to boot on it, then format these partitions.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by cbowman57 on 2011-08-28
Unless you really just want to reinstall Ubuntu all you'd have to do is boot the liveCD, use Gparted to delete the partition of the non-working install, then enlarge the working Ubuntu partition.

Run sudo update-grub when you boot back into Ubuntu and everything should be fine.

---

### Post by Sef on 2011-08-28
**Back up** your operating system first with [clonezilla]("http://clonezilla.org"). No 100% guarantees exist that all will go well.

---

### Post by cbowman57 on 2011-08-28
> **Sef said:**
> **Back up** your operating system first with [clonezilla]("http://clonezilla.org"). No 100% guarantees exist that all will go well.

Very good advice, we rarely think about having a method to backup & restore, until we need it.  By then it's too late. :)

---

