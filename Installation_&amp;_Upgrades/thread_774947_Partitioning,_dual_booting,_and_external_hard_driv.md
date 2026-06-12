---
title: "Partitioning, dual booting, and external hard drives"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by cloroxmartini on 2008-04-29
Alright, I'm pretty new to Ubuntu.  I want to install it on my laptop and set up a dual boot.  This is, however, where I ask a few question.

Would it be possible to set up Ubuntu on a portable drive and then dual boot?

Or would it be better to set up a dual boot using the internal HD and use the portable HD for storage?

Can you partition a portable HD or can it only be used by on OS once it's been formatted?

Here's a little info on the equipment I'm using...
My laptop is a Toshiba Satellite M115 and the portable HD I bought is a SimpleTech 160GB 2.0. drive.

Any suggestions and opinions would be welcome.

---

### Post by kk0sse54 on 2008-04-29
You need to check your BIOS to see if you can boot from an external HD but never the less i suggest partitioning your internal hard drive and use an external as storage as long as it's in a file format that ubuntu can read and write to.

---

### Post by picopir8 on 2008-04-29
Yes, you can easily put the liveCD on a USB HDD or USB flash stick and boot from it (so long as your BIOS allows you).  Search "ubuntu usb flash".

The second option would probably be better if you want a fully functional install w/o having to make lots of tweaks.  If the liveCD is put on a USB drive, then you also need to set up another partition to remember changes because you cant write to the liveCD image.  Its not difficult to do but may be a bit much for someone learning linux.

You can adjust partitions after the OSs are installed using gparted.  The only problem is windows does not play nicely with other OSs so if you ever need to reinstall windows, you will probably have to reinstall any other OS you have installed on that drive.

---

### Post by cloroxmartini on 2008-04-30
So once I install Ubuntu on the internal (which the Ubuntu installers helps set up a partition, correct?) I can go in and partition that external so that both XP and Ubuntu can use it?  How do you do that?

---

### Post by mikewhatever on 2008-04-30
> **cloroxmartini said:**
> So once I install Ubuntu on the internal (which the Ubuntu installers helps set up a partition, correct?) I can go in and partition that external so that both XP and Ubuntu can use it?  How do you do that?

You can simply use that HDD as is. GNU/Linux OSs today can handle most of the proprietary file systems, such as ntfs, for example.
In case you still want to partition it for some other reasons, get GParted Live CD.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by cloroxmartini on 2008-04-30
Alright, thanks.  This was all easier than I thought it was going to be.

---

