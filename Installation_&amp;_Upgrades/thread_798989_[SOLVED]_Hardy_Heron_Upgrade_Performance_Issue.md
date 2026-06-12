---
title: "[SOLVED] Hardy Heron Upgrade Performance Issue"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by jtrindle on 2008-05-18
My Hardy Heron upgrade has gone relatively smoothly, from what I read on this site.  However, I ran into problem when I ran two large things at once, such as MythTV and Firefox.

The load average would shoot up to 35, the system was extremely slow to respond.  I'd eventually give up and reboot.

I dropped back to Firefox 2 with no improvement.  I switched to the RT kernel with a small improvement in time slicing but still unusable loads.

Finally I noticed the readout from "top" seemed to indicate there was no swap in use.

I found that the fstab file was referring to the swap partition by UUID, but this UUID *changed* in the upgrade process.  Once I changed it to /dev/sda5 instead of the UUID, I was able to mount the swap with swapon -a.  Now I can run MythTV and Firefox 2 at the same time (and am doing so right now).  I was not using my 1 GB swap partition at all, and the system was thrashing when running out of my real 512MB RAM.

Right now with MythTV tuned to live TV, and Firefox 2 with 1 tab full of Fark.com's Caturday thread and the other tab containing this post, I have a load of about 2.5.  My swap partition is about half used. It's fully responsive.

So, check that swap!  Use top.  If the swap line appears like:

Swap:  0k total,   0k used,   0k free,   177584k cached

your swap partition is not being turned on.

---

