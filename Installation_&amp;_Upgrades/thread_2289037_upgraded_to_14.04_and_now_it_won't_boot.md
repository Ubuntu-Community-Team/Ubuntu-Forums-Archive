---
title: "upgraded to 14.04 and now it won't boot"
date: 2015-07-31
forum: Installation &amp; Upgrades
---

### Post by Jim_Coker on 2015-07-31
Last night I ran the upgrade to 14.04 only to discover this morning that the laptop wouldn't boot.  Since the laptop has Nvidia, I tried reinstalling gdm and running "dpkg-reconfigure lightdm" to set the server to lightdm since one post on the web suggested gdm had issues with this video chipset, but that didn't help.  It currently hangs after "Stopping Mount network filesystems    [OK]".

I really need help.  I don't want to have to reinstall the OS.

---

### Post by Jim_Coker on 2015-07-31
It appears to be complaining about the START_REMOTETRX and START_SVXLINK variables in init.d/remotetrx and svxlink-server respectively.  Is something wrong with the package(s) containing those scripts?

---

### Post by Jim_Coker on 2015-07-31
While those two undefined variables are causing the startup scripts some indigestion, I no longer believe that is the cause of the failure to boot.

I also found an "acpi" script link in rc2.d that was broken.  Removing it didn't help.

Still searching for something downstream...

---

### Post by Jim_Coker on 2015-07-31
I've now disabled EVERYTHING in rc2.d and it still hangs.  Someone please tell me where to look for the cause!!!

---

### Post by Jim_Coker on 2015-07-31
More info:

/var/log/upstart/mountall.log shows problems mounting swap
/var/log/upstart/network-manager.log shows lots of GLib-WARNING messages saying something about "GError set over the top of a previous GError or uninitialized memory" and suggests there's a "bug in someone's code".
/var/log/upstart/modprobe says "FATAL: Module rtc not found."
/var/log/upstart/module-init-tools.log shows the same problem.
/var/log/upstart/gpu-manager.log shows "update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf" and "/etc/modprobe.d is not a file"
/var/log/upstart/cups.log shows "cupsd failed to create /var/run/cups/cups.sock, skipping automatic printer configuration"
/var/log/upstart/systemd-logind.log shows "/proc/self/fd/9:  4:  ulimit:  error setting limit (Invalid argument)"
/var/log/upstart/modemmanager.log shows "Couldn't find support for device at '/sys/devices/pci000:00/0000:00:1c.3/0000:04:00.0' not supported by any plugin"

This upgrade sounds pretty screwed up.  Can someone tell me how to revert it?

---

