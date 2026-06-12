---
title: "dual boot"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by charlie180 on 2007-08-14
hi  im trying to install dualboot  from ubuntu ultimate 1.4 dvd from the in stall on desktop ..i have a 80gb hard drive split into 2 partions  c: and d  :c; is  25gb running xp, when i install it asks me to install entire disc 80gb guided is this right i dont want to lose my xp for now  cheers

---

### Post by tehshay on 2007-08-14
no, using entire guided disc would erase the whole drive including your current installed operating system, try to look for another options, "manually" or so.

---

### Post by bulldog on 2007-08-14
Choose manual partition.
Now you have some choices to make,do you want a separate home partition for your personal stuff or not.
Let's say you want a separate home.
Create one partition of about 5-10GB  for your /  root partition.
Create a 1GB partition as swap file.
Create the rest of your free space for a /home partition.
It doesn't matter if you make primary or logical partitions,but be absolutely sure your windows will stay on the FIRST PRIMARY PARTITION,otherwise your heading for boot trouble.

---

