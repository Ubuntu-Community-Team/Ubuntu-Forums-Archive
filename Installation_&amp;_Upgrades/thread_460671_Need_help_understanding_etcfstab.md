---
title: "Need help understanding /etc/fstab"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by JoeS on 2007-05-31
Using Ubuntu 7.04
Computer: Dell Optiplex GX100

Can someone help me make sense of this file? 

I don't recognize it from Ubuntu 6.10.
Is there a problem with the install.  The installation disk listed the hard drive as SCSI.  I'm not sure that's right, but it didn't give me any other choices.  In Ubuntu 6.10 the hard drive was listed as hda.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ce0c7602-9ab5-4ad0-8f61-a23601a49247 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=55cab43a-d848-4aca-bb3f-fcb42827a743 /home           ext3    defaults        0       2
# /dev/sda2
UUID=7f8b0a41-8c5a-461b-8dc9-f4da26663f98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by merlinus on 2007-05-31
This is correct with original feisty, but with the kernel upgrade (-16) it reverted back to hd's.

As long as the UUIDs are correct, I have found that it does not matter.

-merlin

---

