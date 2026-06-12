---
title: "Lockup after twenty seconds (or so)"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by froman2686 on 2007-09-17
My computer locks up using the ubuntu gnome desktop.

When I was attempting to install, it'd lock after roughly 10 minutes of use. I had to get the alternate cd and install via text, which had no problems.

Now, in the complete installation, I'm still encountering the same issue. Complete system lockup in about ten-twenty minutes, forcing a hardware reset. I ran a memtest but that came up clean...I'm thinking maybe it's something to do with my video drivers, since it only happens in a GUI?

Hardware:

ASRock Dual-939 Sata II Board
AMD Athlon 64 2200+
2GB Kingston DDR Ram
WD Caviar 320GB SATA hard drive
PNY GeForce 7300 GT

---

### Post by Pumalite on 2007-09-17
Post:
df -h

---

### Post by froman2686 on 2007-09-17
Had to use recovery mode, hung two or three times before I could even put in my login name...

Filesystem     Size        Used      Avail     Use%     Mounted On
/dev/sda1       288G      2.0G       272G      1%         /
varrun            1014m    12k        1014m     1%         /var/run
varlock           1014m     0          1014m     0%         /var/lock
procbususb   1014m    80k        1014m     1%        /proc/bus/usb
udev               1014m    80k        1014m     1%       /dev
devshm          1014m    0           1014m      0%       /dev/shm
lrm                  1014m    33m       9891m     4%   /lib/modules/2.6.20-15-generic/volatile

---

### Post by Pumalite on 2007-09-17
Sorry; not what I thought.

---

