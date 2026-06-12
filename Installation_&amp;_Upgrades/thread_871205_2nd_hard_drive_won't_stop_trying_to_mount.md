---
title: "2nd hard drive won't stop trying to mount"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by noobuntoo on 2008-07-26
I had ubuntu 7.04 for a while and decided to upgrade to 7.10. My system is set up so that it has 2 internal hard drives. One i use for windows and one i use for ubuntu. Normally with 7.04, i would pick ubuntu in GRUB, it loads up and i have access to both hard drives.

After upgrading to 7.10, i noticed it kept making a sound as if it was trying to access my second internal hard drive (the one for windows).

Back when I had 7.04 it made this same sound 2 or 3 times as ubuntu was loading. I'm guessing cause it would automount it as ubuntu loaded. Now it makes it every 3 seconds continuously without end. 

Looking in the folder i can see the drive, removing it isn't an option. If i try to mount it, then it tells me mount failed: Device or resource busy

I really don't mind not being able to access it, but the noise is getting on my nerves and for some reason it slows down everything i do in ubuntu.

Anybody that can help me or point me in the right direction to make this stop?

---

### Post by Yannick Le Saint kyncani on 2008-07-26
> **noobuntoo said:**
> After upgrading to 7.10, i noticed it kept making a sound as if it was trying to access my second internal hard drive (the one for windows).

Hi noobuntoo, I'd suggest you check your logs with "dmesg" just after a sound has been made and look for errors, that would be my first step.

Cheers.

---

### Post by noobuntoo on 2008-07-26
ok did that. i get about 4 million of these

[ 2695.047951] device-mapper: ioctl: error adding target to table
[ 2695.048127] device-mapper: table: 254:1: linear: dm-linear: Device lookup failed
[ 2695.048130] device-mapper: ioctl: error adding target to table
[ 2695.048290] device-mapper: table: 254:1: linear: dm-linear: Device lookup failed
[ 2695.048293] device-mapper: ioctl: error adding target to table
[ 2695.048477] device-mapper: table: 254:1: linear: dm-linear: Device lookup failed
[ 2695.048480] device-mapper: ioctl: error adding target to table
[ 2695.048657] device-mapper: table: 254:1: linear: dm-linear: Device lookup failed

---

### Post by Yannick Le Saint kyncani on 2008-07-26
Yeah, should have specified to google for the error message. Did that, apparently, removing all *evms* packages make the issue disappear. Hope it helps.

---

