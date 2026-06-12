---
title: "&quot;MAKEDEV video&quot; problem"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by jodsalz on 2005-07-08
Hi,

I need /dev/video0 and already tried

$ cd /dev
$ sudo MAEKEDEV video

but nothing happened.

"video" and "videodev" are listed when typing

$ lsmod

When doing

$ MAKEDEV video

(not "sudo...") I get a long error list ("failed" / "no rights...") - so here it tries to do; with "sudo MAKEDEV" it seems it does not even try.

Any ideas?

---

### Post by alastair on 2005-07-08
This might be something you could use a udev rule to do - but what real device is /dev/video0?

Check the syslog and see what the kernel says about this "video" device. If you know the right major/minor numbers then it will also be fairly easy to create the device.

---

### Post by jodsalz on 2005-07-09
[QUOTE=alastair]This might be something you could use a udev rule to do - but what real device is /dev/video0?

Check the syslog and see what the kernel says about this "video" device. If you know the right major/minor numbers then it will also be fairly easy to create the device.[/QUOTE]


Sorry, could you explain this a bit more exactly? Where exactly can I find the major/minor numbers?

I also need /dev/vbi...

Thanks!

---

