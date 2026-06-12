---
title: "[SOLVED] What is /dev/mapper ?"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by dbyrne on 2007-12-21
As subject: what is /dev/mapper all about ? (or where can I find out ?)

In particular, why does my root partition mount on /dev/hda1 (as I would expect), whereas my home partition mounts on /dev/mapper/hda6, not /dev/hda6 ?

$ cat /etc/fstab
UUID=e9c80c92-b11f-4880-ae57-b72da416c012 / ext3 defaults,errors=remount-ro 0 1
UUID=82dd53c2-2930-42c4-ac3a-840f9911eba4 /home ext3 defaults,errors=remount-ro 0 1

$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
/dev/mapper/hda6 on /home type ext3 (rw,errors=remount-ro)

---

### Post by RemmyLee on 2007-12-21
[This]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)") might be of some interest to you.

The short answer is that Linux sees some HDDs as being attached to a RAID controller. If your system is running okay, it's really no harm to you. However, if there are problems, you may wish to reinstall and pass **linux nodmraid**. This most commonly happens with SATA drives. The BIOS incorrectly sees it and instead of doing the check itself, Linux uses the BIOS setting.

As I said, if everything is working okay, don't even worry about it.

---

### Post by dbyrne on 2007-12-21
Thanks, very useful. Funnily enough the main reason I wanted to check is that I'm installing a second drive tonight to RAID onto the first one. It strikes me that even though everything is working now, it might not be afterwards if the system is a bit confused ...

---

