---
title: "Move an install to another partition (Hardy)..."
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2011-11-15
Anybody know which files are necessary to move a Hardy install to another partition, on another disk?

I COULD do it if the new partition was BIGGER - cp  /dev/oldinstall  /dev/newinstall - but it ain't bigger...

Help?


(*of course*, *feel free to ask me why I use Hardy, to tell me also about the distro that you use, what  it does, what you had for breakfast, your favorite  color, and other stuff that doesn't matter to anyone, all with out  answering the question *:lolflag:  :lolflag: :lolflag: )

---

### Post by darkod on 2011-11-16
Are you talking about moving an image to a smaller partition? Because if you want to simply move to another partition using the same computer/hardware, that's possible.

Take a look at FSArchiver. It creates a backup of your partition which can be restored to another partition as long as the destination is bigger than the data size (but it doesn't have to be bigger than the source partition).

It can be installed as stand alone program but because the partition you're backing up need to be unmounted during backup, you can't use it from your running system. In that case you can download and use the System Rescue CD, it includes fsarchiver.

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by Moozillaaa on 2011-11-16
Thanks - that's exactly what I was looking for...

---

### Post by darkod on 2011-11-16
One thing I forgot to point out: I believe grub is looking for the boot files in a particular physical location. The restore will not put them on the exact physical location.
In case you are planning to restore to the same disk, and it doesn't boor straight away, reinstall grub to the MBR first and it should be fine.
If you are restoring to another disk you will probably need to reinstall grub anyway.

---

### Post by Moozillaaa on 2011-11-17
> **darkod said:**
> One thing I forgot to point out: I believe grub is looking for the boot files in a particular physical location. The restore will not put them on the exact physical location.
In case you are planning to restore to the same disk, and it doesn't boor straight away, reinstall grub to the MBR first and it should be fine.
If you are restoring to another disk you will probably need to reinstall grub anyway.


GRUB2 probably** IS** looking for a particular location, but I think legacy GRUB/Hardy 8.04 might not...

I got the re-location done (multiboot), and GRUB behaved well. Of course, XP was unhappy loading from a different disk, and different channel SATA -> IDE slave...

Thanks again there...

---

