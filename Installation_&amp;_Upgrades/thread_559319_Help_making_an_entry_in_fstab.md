---
title: "Help making an entry in fstab"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by sexcopter on 2007-09-25
Hi, I'm hope this isn't a too daft post to be making. I have come across some free space on my harddisk just before my root partition. I can't seem to make the partition grow "backwards" to fill the space using gparted, but I thought "no matter, I can just make a new ext3 partition and mount it in my home folder, right?" Well I'm not too familiar with all this, but it seemed that mounting it in /home/james was a *bad* idea, and it basically screwed up. So I could mount it in a folder in home, /home/james/stuff and that seems to have worked. So here are a few questions:

1. Is it really not possible to grow a partition to the left, or to merge two ext3 partitions?

2. In fstab, what option should I be issuing with the "new" partition to make it writable for me (without sudo'ing etc)?

3. For neatness, is it possible to just mount it in home or / safely and yield what is effectively a similar result to q1?

And just for reference, my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=8ea98640-563b-4a5e-96d6-b29f039318bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=e3c9b69a-f445-4d0f-831d-c33c876028d6 none            swap    sw              0       0
# /dev/sdb4
UUID=35493b47-b48d-4f44-8258-baec3a047ef1 /home/james/stuff/    ext3    defaults    0      0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Where sdb4 is the new partition. I just copied 0   0 from the entry for other lines, and am not entirely sure what it signifies.

Any info on the topic much appreciated. Thanks!

---

### Post by gareththered on 2007-09-25
I´ve just adjusted my partitions, but instead of using gparted on the boot CD or parted command line version, I downloaded the gparted liveCD (google it).  I found this far more reliable as Ubuntu seems to want to mount your drives when gparted seems them, and consequently makes it more difficult to manipulate.
To make use of the space to the left, move the partition to the left, then expand it to the right.
Hope this helps.

---

### Post by sexcopter on 2007-09-26
This is a great idea. I've used gparted livecd before, and am not quite sure why I didn't think of this before. Of course I can't play with the root partition---it's mounted! (duh!)
I won't go into detail but the gparted livecd isn't working for me right now (need to change a graphics card, don't ask), but I'll give this a go once I get my new gfx card installed.

Many thanks!

---

### Post by gareththered on 2007-09-27
I had similar issues with the liveCD on an Intel video chipset latop. (965 I think).  It's a case of getting the right options at boot time, and using the VESA driver.
It's all very hit and miss.  Good Luck!!!!

---

