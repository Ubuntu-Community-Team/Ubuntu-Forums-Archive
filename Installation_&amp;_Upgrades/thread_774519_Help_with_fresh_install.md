---
title: "Help with fresh install"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by kmullinax on 2008-04-29
This is a complete n00b question... 
I haven't ever had to overwrite my existing install with a fresh one, but it looks like I have to now, as my attempting to upgrady to Hardy was a disaster.
My current setup has my /home as a separate partition from my root, and there's a lot of data in there I don't want to lose.
How do I tell the software during a fresh install to use the existing /home directory instead of overwriting it or creating a new one?

Thanks!

---

### Post by Bunro on 2008-04-29
Use the alternate installation disk. At one stage you can manually select how you want to partition your disk. here you can select / (root) for fresh partition (re format) also you can select that you want to keep/ re-use your home dir.
The "best" is to have your disk with 3 partitions /swap (2x the your RAM size), / (root), /home.

Regards, Robert

---

### Post by ianhaycox on 2008-04-29
Using the normal install disk you can select the manual partition option and choose the appropriate partitions for root (/) and /home just ensure that you do not tick the format box for the /home partition.

Alternatively just install and format a fresh install and then fix /etc/fstab later to use your existing /home on the other partition. Make a note of your current fstab file before installing just in case.

Usual caveats, make sure you backup and verify your safe data first.

---

