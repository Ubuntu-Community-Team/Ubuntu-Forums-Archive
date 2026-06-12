---
title: "wirelss and touchpap stopped working after 11.04 upgrade"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by hellishheat on 2011-09-24
Hi,

I'm a linux newb. I upgraded to 11.04 after 1 week of bliss with 10.10. Now my wirelss and touchpad don't work.

I'm more concerned with the wireless for now.

Toshiba Satellite Pro
Intel Corp PRO/Wireless 3945ABG

I noticed that some users were asked to return  the output of these commands for similar problems:

rfkill list -- returns nothing!
dmesg | grep iwl -- returns nothing!

I tried this bit of advice:

sudo modprobe lwl3945
FATAL: Could not load /lib/modules/2.6.38-100generic/modules.dep

Can someone please help?

---

### Post by LinuxFan999 on 2011-09-24
If you have another computer, you could find and download the driver online, then copy it to a flash drive, then connect it to  your laptop and install the driver. if you get your WiFi working, then you could try downloading and installing a driver for your touchpad. If Installing drivers doesn't help, or if you don't know how to install drivers, then your only option is to back up and do a clean re-install of Ubuntu.

---

