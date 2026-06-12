---
title: "Install only GRUB?"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by linj on 2005-12-06
Is there a way to install only GRUB bootloader from the install CD or live DVD? PartitionMagic corrupted away my extended partition with boot/swap partition into one dead mold of partition. The boot partition was a remnant from a Gentoo installation, and I don't have a copy of the grub.conf, so I thought that it would be easier to have an auto-install of GRUB. 

So is there a way to just skip to GRUB bootloader installation on the CD? Expert mode doesn't help any...

Any help is much appreciated!

Oh, and I have Windows and Gentoo on the same disk, and after fixmbr, I can boot into *something*, but it's... just Windows.

---

### Post by earobinson on 2005-12-06
I did a google search for (reinstall grub ubuntu) and i found this [http://ubuntuforums.org/archive/index.php/t-76652.html](http://ubuntuforums.org/archive/index.php/t-76652.html)

Weird that i couldent find it just by searching the forums but at least i found it

---

### Post by linj on 2005-12-06
Thanks! I just sighted that, but it seems a bit risky.. I'm not sure if it'll wipe over my files, no?

I'll give it a try. It can't break a non-reachable OS more.

---

### Post by bwog on 2005-12-06
This is faster and easier: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)

(though the above method workd, Ive tried it.)

---

### Post by frodon on 2005-12-06
To re-install GRUB (only) : [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

