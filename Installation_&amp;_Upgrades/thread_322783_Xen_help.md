---
title: "Xen help"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by jamiekao526 on 2006-12-21
hello, I need help with installin xen, I followed the guide [https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy](https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy)

It worked till the point where I have to reboot into the new xen kernal.

However when it's booting, it's stuck at 'waiting for root' and the hotplug dectection screen (which I solve by disconnecting my usb mouse).

any help would be appreciated

---

### Post by jgoor on 2006-12-27
the path prefixes from your Xen stanza in 'grub.list' must have '/boot/'. Possibly -due to a bug- this is not the case. I got the same error once and after manually adding '/boot' before the paths in the stanze it worked like a charm!

@edit: I mean '/boot/grub/menu.lst'

---

