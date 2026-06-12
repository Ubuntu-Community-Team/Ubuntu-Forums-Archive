---
title: "/media/sdb2 not ready or not present error on Ubuntu 10.04RC"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by cgraham on 2010-04-28
I keep getting an error message on Ubuntu 10.04 RC during boot up that says, "The disk drive for /media/sdb2 is not ready yet or not present". Then it says," Continue to wait; or Press S to skip mounting or M for Manual recovery" The computer has only 1 hard drive and a DVD-RW drive installed. There were no usb drives plugged in during the install.

Does anyone know of a fix for this?

---

### Post by mikewhatever on 2010-04-28
You can probably boot from the cd. If so, it would be interesting to look at your fstab.

---

### Post by cgraham on 2010-04-28
The Ubuntu 10.04 RC live cd will not boot. I have downloaded it 4 times and burned 4 cd's. They all gave an install error and rebooted. I had to use the alternate install cd.

I will try to get a look fstab.

Thanx

---

### Post by cgraham on 2010-04-28
_**SOLVED**_

Hey, thanx. i looked at fstab and found a line referring to sdb2. I deleted it and now my computer boots fine.:P

---

### Post by mikewhatever on 2010-04-29
> **cgraham said:**
> The Ubuntu 10.04 RC live cd will not boot. I have downloaded it 4 times and burned 4 cd's. They all gave an install error and rebooted. I had to use the alternate install cd.

I will try to get a look fstab.

Thanx

Downloading multiple times is ..., well, stupid.;) Use md5sum next time.

---

