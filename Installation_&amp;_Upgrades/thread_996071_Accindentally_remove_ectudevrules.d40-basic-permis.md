---
title: "Accindentally remove /ect/udev/rules.d/40-basic-permissions.rules"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by henrik65 on 2008-11-28
Hi,

I wish my fist post was more impressing, but I managed to remove
/etc/udev/rules.d/40-basic-permissions.rules
a few minutes ago.
I'm new to ubuntu but has non-Linux unix experience.
I run Ubuntu 8.10.

Can someone please explain how I download a new one? Where?

Thanks,
  Henrik

---

### Post by oldos2er on 2008-11-28
Here's mine, I haven't changed it from the default:

# This file establishes permissions and ownership of devices according
# to Ubuntu policy.  See udev(7) for syntax.
#
# The names of the devices must not be set here, but in 20-names.rules;
# user-friendly symlinks (which need no permissions or ownership) should
# be set in 60-symlinks.rules.

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",        MODE="0664"

# vc (virtual console) devices
SUBSYSTEM!="tty", GOTO="vc_end"
KERNEL=="console",            MODE="0600"
KERNEL=="ptmx",                MODE="0666"
KERNEL=="tty",                MODE="0666"
LABEL="vc_end"

# Miscellaneous devices
KERNEL=="null",                MODE="0666"
KERNEL=="zero",                MODE="0666"
KERNEL=="full",                MODE="0666"
KERNEL=="random",            MODE="0666"
KERNEL=="urandom",            MODE="0666"
KERNEL=="inotify",            MODE="0666"


 Hope this helps.

---

### Post by henrik65 on 2008-11-28
Thanks! Didn't dare to reboot until I restored the file (but I really don't understand the importance of the file).

Again, many thanks!

Regards,
  Henrik

---

