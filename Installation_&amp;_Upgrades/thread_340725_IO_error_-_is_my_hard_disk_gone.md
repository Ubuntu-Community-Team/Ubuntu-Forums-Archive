---
title: "I/O error - is my hard disk gone?"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by sikandarinux on 2007-01-17
Hi,

please help me maybe I have to change the disk I have time before the end of the week!

I installed ubuntu 3 days ago on a new USB external Western Digital 120GB HD. Then I installed nvidia drivers - everything ok, and finally 3d desktop, but it wasn't working properly. So I unistalled the 3D and nvidia drivers, but some problems came, like "read only filesystem" errors or the X server which couldn't start, and one time a "I/O error".
So I decided to re-install the whole ubuntu, and did it with the alternate install CD.

Now I can't partition my hard disk properly, it took me like 4 times to make partitions and format and I managed to install ubuntu but it loads and hangs when the kernel checks the usb disk.

Right now I'm trying to use the ubuntu alternate install cd again, but it hangs on syslog-klog loading. ONLY IF I boot with the install CD in - without the external drive connected - and start install I'm able to go on. I put my local area information and then plug in the ext drive, but when it started partitioning I got another I/O error.
I'm really worried about this, although it seems I can format and partition the drive correctly under winXP.

Should I change my drive?

---

### Post by lotacus on 2007-01-17
You said this is a usb drive? Well, I would first run a thorough scan disk on the drive in windows. I hope you know how to do this. You will want to check for bad sectors. This will take hours to complete. If you don't want to do that (even though you should), you can always start copying lots of big files over to the drive while in windows. If you don't get any errors, then all may be fine. If you still have problems in linux, then it could have something to do with the drivers for linux.

---

### Post by sikandarinux on 2007-01-26
Thanks, the drive wasn't working properly, I changed it.

---

