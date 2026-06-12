---
title: "Dual-Boot Question"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by Ephemeriis on 2006-07-29
I intended to run Ubuntu exclusively, and ditch Windows entirely.  Because of that, I installed Ubuntu on a fresh HDD, without my old Windows drive connected at all.

I have since discovered that many of my games just don't work correctly through Linux/WINE, and I'm having to boot up my old Windows HDD to play them.  This isn't a problem, but it is inconvenient.

At the moment, I have two HDDs, each with its own bootloader in the MBR.  If I want to run Linux, I unplug the Windows HDD...and if I want to run Windows, I unplug the Linux HDD.  You get the idea.

How can I consolidate this?  How do I go about adding Windows to GRUB, or Ubuntu to the Windows bootloader?  Is there an advantage to using GRUB over Windows bootloader, or vice-versa?

---

### Post by confused57 on 2006-07-29
See if this thread might be an option:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Ubuntu would be master drive and Windows as slave...it's how I have my system(s) set up.  This way, all you need to do is add the Windows entry to the Ubuntu grub menu.lst...your Windows isn't affected at all.

---

### Post by Ephemeriis on 2006-07-29
Thanks, that actually looks **very** helpful.  Would probably have saved me the trouble of posting at all if I'd seen that first...

Another question, then, since I'm already replying.  If I've got GRUB as the bootloader, will I still have the same options launching Windows that I normally would - such as Safe Mode?  I'm assuming that I see GRUB first, choose Windows, and then can hit F8 for options like normal - correct?

Just curious...  I suppose I'll find out soon enough.  ;)

---

### Post by Ephemeriis on 2006-07-30
Well, that didn't work.

This is the output from an fdisk -l.
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9348    75087778+  83  Linux
/dev/sda2            9349        9726     3036285    5  Extended
/dev/sda5            9349        9726     3036253+  82  Linux swap / Solaris

Disk /dev/hda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5168    39070048+   7  HPFS/NTFS
```

If I'm reading this correctly...  Ubuntu is on hd0, and Windows is on hd1 - correct?  So, in my menu.lst where I have...
```
title           Microsoft Windows XP Professional
rootnoverify	(hd1,0)
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```
...it should work, right?

Whenever I try to boot into Windows it just hangs.  I don't get any errors, no messages or anything like that...but nothing boots.  The GRUB menu disappears, the screen goes black, and I get nothing.  I've tried it both with "root" and "rootnoverify" - doesn't seem to matter.  I've looked over several other threads now, and everyone else seems to be using this exact same config with success.  Any idea what I'm doing wrong?

Alternately, if I can't convince GRUB to boot Windows...is there some way to use the Windows bootloader to boot Ubuntu?

---

### Post by confused57 on 2006-07-30
Sorry it didn't work.  Your menu.lst Windows entry looks like it should work, SATA drives can be frustrating with Linux.
Yes, I haven't done it myself, but you can use the Windows boot.ini to dualboot.  I did a forum search for boot.ini and found this link:

[http://www.ubuntuforums.org/showthread.php?t=101398&highlight=boot.ini](http://www.ubuntuforums.org/showthread.php?t=101398&highlight=boot.ini)

Added:  I won't bump this thread, but great to hear you got your dualboot working, I knew everything looked like it should.  Thanks for the update.

---

### Post by Ephemeriis on 2006-08-01
Actually, it looks like the issue was with my Windows HDD.  Midway through playing with all this, Windows started having trouble booting on its own, even when it really was the primary master.  Wound up imaging it over to a new HDD, and GRUB is now happily booting both drives.

Thanks for all the help!

---

