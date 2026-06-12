---
title: "How to install Ubuntu 11.04 on a Macbook Pro 8.1"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by dracotux on 2011-10-15
Dear Ubuntu guys,

I have a Macbook Pro 8.1 early 2011. I want to run Ubuntu 11.04 on it.

I tried to follow this link to install it:
[http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/](http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/)

It boots the system, but when I start the install, the problem surfaces.

Afther I selected my language, the next prompt is to download updates while installing. Since the driver for the Mac wireless card isn't supported by default, I don't check any of the boxes and hit the Continue/Install button. 

This is where it fails: it gives a System Program Error Reported. Do you want to report the problem?

I choose no, for obvious reasons. I can't get passed this error. I tried different ISO's, but it doesn't make any difference. A live CD doesn't work on a MBP 8.1, this gives a initramfs problem.

Can anybody help me out?

---

### Post by lsward on 2011-10-15
Have you tried hooking it up to an ethernet connection?  That's what I do when I install on a new computer because the wireless always takes some fooling around to get working.  I would try a hardline connection and then figure out the wireless.

---

### Post by dracotux on 2011-10-20
I found what was wrong after a tip from a friend of mine. You need to convert the partitions to ext4 with gparted, before you start the installation. That's it. After I did that, the install went fine. The next problem is how to boot it (refit, mac, etc.), but that's for another topic.

Thank you for all the support!

---

