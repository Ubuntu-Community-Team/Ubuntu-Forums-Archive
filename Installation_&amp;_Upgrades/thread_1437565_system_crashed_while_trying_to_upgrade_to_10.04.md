---
title: "system crashed while trying to upgrade to 10.04"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by arjunak01 on 2010-03-24
i was trying to upgrade to 10.04 (from 9.10 x86_64)when the update manager crashed without any warning or errors. it happened while the packages were being installed, as a result of which i could no longer login into gnome. so i logged in using the terminal and since i had cleaned the cache before upgrading i ran *sudo -i dpkg *.deb *(there were a large number of deb files in it, so i thought those were the upgrade packages)  but the process couldn't be completed. it said that there were too many errors. after rebooting, gnome doesn't start and i can see *lucid development version *in the terminal. it also didn't detect my usb keyboard. how do i fix it ?do i have to reinstall ubuntu

---

### Post by mikewhatever on 2010-03-24
Try running **sudo apt-get update && sudo apt-get upgrade**
Perhaps it will then finish downloading the new packages.

---

### Post by krige on 2010-03-24
I have the same problem: the update manager crashed without any warning or errors.

The appearance of the user interface is still the old 9.10 one but by running "lsb_release -a" I get the following output:

```
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid
```

If I run "top" I get the following output:

```
u(s): 59.9%us, 39.4%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:   1026464k total,   977800k used,    48664k free,    63180k buffers
Swap:  3004112k total,     3504k used,  3000608k free,   617292k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6918 root      20   0  126m  43m  14m R 94.7  4.4  29:56.21 lucid
 4939 root      20   0  229m  48m 8436 S  3.6  4.8  20:34.77 Xorg
16192 krige  20   0 38028  13m 9692 S  1.3  1.3   0:00.93 gnome-terminal
 5202 krige  20   0 29756  19m 6760 S  0.3  1.9   0:36.79 compiz.real
```

It looks like the lucid process is still working, maybe still upgrading but not showing any dialog window.

Should I wait a while and see what happens or do something?

---

### Post by krige on 2010-03-24
After waiting about 3 hours I killed the lucid process, then I ran:
```
sudo apt-get install -f
```
It installed several packaged then ended with the following:
```
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
.: 4: Can't open /scripts/functions
```

I then rebooted and run the Update Manager which installed several other packages and in the end asked me to reboot, completing successfully the upgrade.

---

