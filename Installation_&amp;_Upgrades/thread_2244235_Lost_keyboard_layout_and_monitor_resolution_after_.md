---
title: "Lost keyboard layout and monitor resolution after upgrading to 14.04"
date: 2014-09-14
forum: Installation &amp; Upgrades
---

### Post by redaxe90 on 2014-09-14
Hi folks

I just finished upgrading my system to 14.04 from 13.10 and upon doing that, I no longer have the Icelandic Keyboard layout available, which is essential to me as it's my native language. I also had the desktop revert back to 1024x768, despite it having been 1366x768 prior to upgrade. How in the world can I find my way through that, since I'm not exactly a wizard on those things?

Partly solved, got the keyboard layout corrected after searching through heaps of options and messing about until something happened. Still don't have the Resolution problems solved. Any idea what may have happened?

---

### Post by redaxe90 on 2014-09-15
```
~# sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:0d.0 ==
vendor   : NVIDIA Corporation
model    : C61 [GeForce 6150SE nForce 430]
modalias : pci:v000010DEd000003D0sv00001462sd00007309bc03sc00i00
driver   : nvidia-173 - distro non-free
driver   : nvidia-304 - third-party free recommended
driver   : nvidia-304-updates - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```

```
~# sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as
'/etc/X11/xorg.conf.nvidia-xconfig-original'
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


```

```
gksudo nvidia-settings

** (nvidia-settings:12436): WARNING **: PRIME: Failed to execute child process "/usr/bin/prime-supported" (No such file or directory)
** Message: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       preopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.


```

After looking at those things, I ran out of understanding, so now I'm completely lost. Can anybody figure this out for me?

---

### Post by redaxe90 on 2014-09-16
After reinstalling all drivers imaginable, this has finally been solved. Resolution is back to what it should be, at least within Gnome. I have yet to see if the same applies to LXDE or the Lubuntu desktops

---

