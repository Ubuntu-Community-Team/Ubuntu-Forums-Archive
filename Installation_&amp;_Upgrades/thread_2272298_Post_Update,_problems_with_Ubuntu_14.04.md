---
title: "Post Update, problems with Ubuntu 14.04"
date: 2015-04-05
forum: Installation &amp; Upgrades
---

### Post by stevecoh1 on 2015-04-05
I took the latest updates that Ubuntu pushed out the other day.  This installed a number of things, most notably a new linux image 3.13.0-48-generic.

Now I find two very annoying problems:

USB doesn't work.  At least, my mouse doesn't work anymore.  It works fine on other computers.  I can turn on my touchpad but I hate the thing.  dmesg shows me errors associated with US[   37.616514] usb 3-7: reset full-speed USB device number 4 using xhci_hcd
[   37.635587] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880211af6e00
[   37.635591] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880211af6e40
[   37.635593] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880211af6e80
[   37.635594] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880211af6ec0


Also, wifi no longer works.  My wifi connections are no longer seen.  I can connect with my wired network, but not with WIFI?

How can I either get back to my previous kernel or fix these issues?

Computer is Lenovo thinkpad T-540p

---

### Post by stevecoh1 on 2015-04-05
OK, this is definitely a problem with the new linux image on my hardware.  Booting instead with the previous kernel via grub makes everything work again.

I'd like to file this as a bug report, but the process is just hideous and I could not figure out how to do it.  Why doesn't the launchpad login screen let you paste your password?

---

### Post by stevecoh1 on 2015-04-06
I've me-tooed onto Bug 1440174 in the Ubuntu system.  Sorry I can't give a link.  Why does the Launchpad system disable copy and paste functions?

---

