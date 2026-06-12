---
title: "Unloading drivers/modules, how?"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by remmelt on 2005-04-14
Hey!

I finally got my wireless card to work! I'm going to create a howto about it, but first I need to know how I remove a module.

For the card to work, I needed to unload the prism54 module with modprobe -r. This is fine and worked well, ofcourse, but now when I reboot, it still gets loaded. How can I remove it completely? There is no sign of it in /etc/modprobe.d/... I don't know where to look!

Thanks!

---

### Post by speedman on 2005-04-14
It may be listed in /etc/modules where you could simply remove the entry, but it is more than likely being loaded by hotplug.  In that case you can blacklist the module by entering it in /etc/hotplug/blacklist.

HTH


Regards,

SM

---

### Post by elempoimen on 2005-08-17
Thanks!  I needed this to get acx_pci out and ndiswrapper in!

---

