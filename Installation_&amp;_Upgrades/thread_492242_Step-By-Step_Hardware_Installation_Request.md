---
title: "Step-By-Step Hardware Installation Request"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by wog on 2007-07-04
I'm looking at installing a second (and perhaps even a third) hard drive to my machine for a /home directory, but the drives were previously used as Windows drives, and I haven't done this sort of thing before with Linux.

What do I do, and in what order?

---

### Post by Arrdee on 2007-07-04
I'm not absolutely positive this is what you're looking for, but it may help:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by wog on 2007-07-04
I think that set of instructions assumes the partition you're creating is going to be in unallocated space on your current drive. Once the new hard drive is in place and formatted, I can use those instructions to move my /home directory, but how do I go about setting up the drive? Do I use gparted, or do I use another program?

The real issue here is the drive may be in NTFS format, meaning I'd need to wipe the drive completely before I can put /home on it. And I don't know which programs in linux do what.

In Dos I'd use fdisk from a floppy or CD, but I don't suppose there's a version of fdisk for linux, is there?

---

### Post by wpshooter on 2007-07-04
If you simply want to WIPE the drives clean then use [www.killdisk.com](www.killdisk.com)

---

### Post by kevinlyfellow on 2007-07-04
Install the new harddrive and then install gparted.  With gparted you can prep the harddrive however you want.

---

### Post by wog on 2007-07-05
gparted. Right.

Thank you for that bit of advice. Just for general reference, do you know if gparted on the LiveCD or is it something I'd have to be online to install? This isn't a problem for this time, but it would be nice to know for later, tackling someone else's system.

No offense, wpshooter, but I think I'll stick to the more common utilities and try to master them first. But I will keep your suggestion in mind. :)

---

### Post by kevinlyfellow on 2007-07-05
> **wog said:**
> gparted. Right.

Thank you for that bit of advice. Just for general reference, do you know if gparted on the LiveCD or is it something I'd have to be online to install? This isn't a problem for this time, but it would be nice to know for later, tackling someone else's system.

No offense, wpshooter, but I think I'll stick to the more common utilities and try to master them first. But I will keep your suggestion in mind. :)

[Gparted livecd right here]("http://gparted.sourceforge.net/livecd.php")!

---

### Post by wog on 2007-07-05
Wow! Thanks!

I know right now this is all looking much more complicated than it actually is. Seeing that screenshot was actually somewhat reassuring. :)

---

