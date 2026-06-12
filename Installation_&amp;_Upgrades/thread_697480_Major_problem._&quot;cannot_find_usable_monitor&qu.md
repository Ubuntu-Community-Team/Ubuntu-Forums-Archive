---
title: "Major problem. &quot;cannot find usable monitor&quot; X grapical interface inoperable"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by GabrieisWings on 2008-02-15
Upgrading from Edgy to Fiesty. Finished the update, did the reset, and as it starts up, it goes...
mdadm: no devices listed in conf file were found

Screen flickers from that to black like it's trying to start the GUI, and then Blue screen with...

"Failed to start X server (Graphical User Interface. Would you like to view details in order to diagnose problem? Yes/No"

If you look the details over it shows the same as mentioned before. It also includes that there is a monitor, but it is...unusable?

Anyone know how to help a poor boy like me through this? :confused: Please?

It showed signs of something like this happening during the update. mdadm kept having problems doing something. I'm not quite sure what, though. It moved too fast.

-S

---

### Post by taurus on 2008-02-15
Try booting into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

