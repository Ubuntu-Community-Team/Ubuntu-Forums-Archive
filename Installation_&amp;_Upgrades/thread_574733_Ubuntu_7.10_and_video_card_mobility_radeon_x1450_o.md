---
title: "Ubuntu 7.10 and video card mobility radeon x1450 on ASUS V2J"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by romarco on 2007-10-13
Hello,
I have a notebook ASUS V2J with video card mobility radeond x1450 and monitor 14 inch 1440x900.
I tried in the past to install Ubuntu 7.04 both 32 and 64 bit without success.
During installation I received an error on startx that no  screens found because not usable configuration. I modified manual the file xorg.conf with driver vesa and all the resolution and depth but the result was the same.
So, I had to install Suse 10.2 (without no problems) but I prefer Ubuntu that I have at home on my desktop PC.
I hope Ubuntu 7.10 was better but I've tried the RC release with the same problems.
Before I install the Suse 10.3 I hope that someone helps me or that the final release (I don't beleave it) solves my problem.
Thanks
Marco

---

### Post by Pumalite on 2007-10-13
Install the driver through ENVY or this: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by romarco on 2007-10-13
But how can I do that during installation?

---

### Post by Pumalite on 2007-10-13
It's done at the end of the installation. If what you have is trouble booting the Live CD, go with the Alternate CD.

---

### Post by romarco on 2007-10-15
OK. Finally it works!
the steps are for other users:
1) Install Ultimate version
2) Install ati driver (Don't work because needs libstdc++.so.5 and not .6 installed)
3) Install libstdc++5 package.

Thank a lot

---

### Post by romarco on 2007-10-15
Of course Alternate not Ultimate

---

