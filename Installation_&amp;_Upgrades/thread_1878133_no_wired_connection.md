---
title: "no wired connection"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2011-11-09
Posted in "Networking" got no replies.

Have Ubuntu 11.04 64bit installed but "no wired network" connection.  It appears that Ubuntu hasn't recognized to my ethernet card (Intel 82579V Gigabit Network card.  If I do a ifconfig all it shows is the loopback.

Appreciate directions for a beginner!  Thanks.

---

### Post by dino99 on 2011-11-09
comment out entries into /etc/network/interfaces

---

### Post by deeppow on 2011-11-09
> **dino99 said:**
> comment out entries into /etc/network/interfaces

No joy.  Didn't help.

I did indicated using the wrong version in case that makes a difference.  It is 10.04-3 LTS.

---

### Post by deeppow on 2011-11-09
Did a "sudo lspci" and a "sudo lsusb" and get the following:

---

### Post by deeppow on 2011-11-10
Included my ethernet controller (Intel 82579V Gigabit Network controller) in my google search and found a link ([http://giantdorks.org/alain/fix-for-non-working-wired-ethernet-on-dell-latitude-e6520-with-intel-82579-based-adapter-running-ubuntu-10-04-lts-lucid/]("http://giantdorks.org/alain/fix-for-non-working-wired-ethernet-on-dell-latitude-e6520-with-intel-82579-based-adapter-running-ubuntu-10-04-lts-lucid/")) that solved my issues.

Beware that system updates might require this to be reinstalled.  After updating the first time, I had to reinstall the drivers.

---

