---
title: "Upgrade from 8.04 to 9.10 lost share name"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by boomcat on 2010-02-09
I upgraded my desktop computer from 8.04 to 9.10 last night.

The second HD, which contains all of my music, used to mount as:

/media/disk/AllMusic

Now it mounts as:

/media/d7c7179f-d775-49ff-889e-661d6d188452/AllMusic

So the music player applications can't find the music, and neither can the other computers on my home network.

Ubuntu won't let me rename it.

How can I fix this and restore this shared drive?

---

### Post by shriramrs31 on 2010-02-09
It is mounting with the default UUID. /etc/fstab file handles mounting. have a look at this tutorial ;-) to make your own entry

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by boomcat on 2010-02-09
I followed the instructions in the tutorial.

I edited fstab to add:

/dev/sdb1	/media/disk	ext4

and this worked for a while - the music player found the music again - but after rebooting the disk is just gone, it is missing. It does not appear anywhere on the desktop or Places.

---

### Post by boomcat on 2010-02-09
I re-edited fstab to read:

UUID=d7c7179f-d775-49ff-889e-661d6d188452	/media/disk	ext3	defaults	0	0

and this seems to have done the trick. It reboots and auto-mounts just fine. Apparently the UUID is important, and I had the disk type wrong: it's actually ext3.

Problem solved. 

Thanks!

---

### Post by shriramrs31 on 2010-02-09
Sooper, Now i too have a new info ;-)

Have fun

---

