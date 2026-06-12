---
title: "Moving an Installation onto USB:"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by tgarrido on 2011-05-29
After quite some time and hassle, I was finally able to install Ubuntu 10 on my Dell 700m and get the graphics card to work.

I was wondering, though, would it be possible to copy the entire installation, now that it is working, to a USB disk, change some parameters, and get the system to be able to boot from USB as well, with the hard drive out of the system?

---

### Post by Herman on 2011-06-11
Yes, you should be able to do that without any trouble at all, and you shouldn't even need to change any parameters.

---

### Post by sbraz on 2011-06-11
yes. i did this after booting from a live distro with **dd if=/dev/sdX of=/dev/sdX bs=4M** ([COLOR="Red"][SIZE="3"]warning[/SIZE][/COLOR], this command might destroy data if used the wrong way).

keep in mind that there are better ways to do it (dd reads used AND empty sectors and doesn't care about drive sizes), and that by using this procedure your copied partitions will have the same UUIDs as the originals so maybe it's better to edit /etc/fstab to use /dev/sdX instead of UUID=XX..XX if you want to use this method for testing.

i've used this method to seamlessly upgrade my hdd and... it worked. :D

---

