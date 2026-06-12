---
title: "downgrading gdm"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by phoenixfire900 on 2010-01-07
when I followed this thread:

[http://ubuntuforums.org/showthread.php?t=1331457](http://ubuntuforums.org/showthread.php?t=1331457)

I got this error when I rebooted:

screen init failed

---

### Post by kansasnoob on 2010-01-07
I similarly broke mine once and to get back to the original gdm I booted into recovery mode (if the grub menu is hidden at boot you'll have to depress the space bar during boot if this is grub2, or the Esc key if legacy grub), then after recovery mode completed running I selected **netroot** (that provides a shell w/networking) from the options and ran:

```
sudo apt-get --purge remove gdm-2.20
```

```
sudo apt-get install --reinstall gdm
```

```
sudo dpkg-reconfigure gdm
```

```
sudo reboot
```

That got me back to the original Karmic gdm, I have not tried changing to the older gdm again since then.

---

