---
title: "Installing new wireless drivers"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by Kevin Klein on 2005-03-12
I'm trying to get my wireless card to work, and sources I've found indicate that I need a newer version of the Atheros/madwifi drivers.

I've successfully downloaded and compiled the driver, but I can't seem to get it installed.  "modprobe -r ath_pci" followed by "modprobe ath_pci" leaves the same driver version number in dmesg.

What do I need to do to install the new driver?

---

### Post by Kevin Klein on 2005-03-13
Never mind.  I figured it out.

Delete the old ath* and wlan directories from kernel/drivers/net.  Then copy the new .ko files to a new directory in the same location.  Then run depmod.

Now to get samba to talk to my XP SP2 machine...

---

