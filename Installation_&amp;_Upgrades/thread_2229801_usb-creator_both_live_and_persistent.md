---
title: "usb-creator*: both live and persistent ?"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by juju43 on 2014-06-15
I tried usb-creator on *ubuntu 12.04 and 14.04 and you can either be persistent, either live.
But It would be better to offer both when enabling persistence.

On my usage, I found that overlayfs doesn't handle well crash/electricity cut or the like unlike ext4, so you have to do a fsck after or being unable to boot. If you are in a rush and don't need anything from persistent image, going back in live mode is the best solution.

That's what makes me prefer using Lili when creating usb boot but needing Windows is a bit...
[http://www.pendrivelinux.com/linux-live-usb-creator/](http://www.pendrivelinux.com/linux-live-usb-creator/)

Any way to do that currently? or open a Feature request?

Thanks

---

### Post by sudodus on 2014-06-15
You can add an entry to the boot menu, so that you have one entry with the boot option **persistent**, and another entry **without persistent**.

A simpler alternative is to change manually (to edit the boot options) at boot time.

A different alternative is to make a installed system in the USB pendrive. Such a system will be more stable and can be updated exactly like any installed system in an internal drive. But for the same reason as in the case of persistent live systems, it will be slow, if the pendrive is slow, but it will be much faster if you use a fast USB 3 pendrive (even in a USB 2 connection to the computer). In all these cases it is very important to let the system flush all buffers before you unplug the pendrive, so have patience during shutdown.

See this link for more details about pendrives and booting from pendrives

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by juju43 on 2014-06-21
Nice trick. Would be nice to have this checkbox in usb-creator.

Same with both legacy/UEFI bios option as described here [http://ubuntuforums.org/showthread.php?t=2108487&page=3&p=12656460](http://ubuntuforums.org/showthread.php?t=2108487&page=3&p=12656460)

---

