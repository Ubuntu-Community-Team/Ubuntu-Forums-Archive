---
title: "Install Issues: X on PCI-e"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by RaffiRai on 2005-05-06
I'm having some issues installing Ubuntu on one of my boxes.  Rather, the install is actually going fine, but when X starts, I'm getting what I assume is a custom error from my monitor, something along the lines of "Improper frame rate: power saving in 15 seconds."

I don't understand that, really.  I've seen the monitor do 100FPS at well over 1024x768, as it has windows installed for gaming.

The box is an [MSI Combo 915G](http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=604) motherboard, 1gb of DDR400, a p4 3.8, and a PCI-e 6600GT.

as I said, the install goes fine, but X crashes the monitor, apparently.  MSI, I love then for my gaming rig, has no support what so ever for Linux, but I've run gentoo and ubuntu on other MSI boards, so I was assuming that they simply wouldn't support you, not that it wouldn't work.. anyways, any help would be greatly appreciated.  thanks.

   -Raffi Rai

---

### Post by RaffiRai on 2005-05-07
No one?

   -Raffi

---

### Post by alastair on 2005-05-08
Might be worth posting the X log and config file i.e.

/var/log/Xorg.0.log
/etc/X11/xorg.conf

---

