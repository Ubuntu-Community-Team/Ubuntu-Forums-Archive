---
title: "switching from nvidia to intel graphics"
date: 2014-06-23
forum: Installation &amp; Upgrades
---

### Post by Roinou on 2014-06-23
Hi all,

I'm having some issues with my graphic drivers. My Nvidia card just died, so I plugged in the screen to the motherboard to use the integrated chipset of my core I5 CPU.
Now, I can't get the graphical interface to work. I tried to reconfigure X and copy the generated xorg.conf file in /etc/X11 with no success. I tried both "vesa" and "intel" dirver, no changes.

I don't really know how to diagnose the problem either. Only weird thing I read in dmesg is "i915 000:00:02.0 registered panic notifier". in Xorg.log, I don't see any major issues, except that it failed to load glx.

Any help on how to diagnose and fix will be greatly appreciated!

thanks a lot

---

### Post by LastDino on 2014-06-23
Did you actually purge Nvidia drivers or not? They do try to load themselves even if card is not there.

```

sudo apt-get purge nvidia*
```

Then remove your xorg.conf and install it again.

Reboot.

---

### Post by Roinou on 2014-06-23
well, I uninstalled the proprietary drivers manually, and to make sure, I added "nvidia" in the modprobe blacklist. Still no success.

Running lsmod doesn't show any module named "intel". I checked, and the driver is installed from official repo though.

I do see some blacklisted modules: "intelfb" and "snd_intel8x0m". But I don't think they have anything to do.

---

### Post by Roinou on 2014-06-24
ok, got it:
[http://askubuntu.com/questions/86465/switch-from-nvidia-to-internal-intel-hd-graphics-opengl-does-not-work](http://askubuntu.com/questions/86465/switch-from-nvidia-to-internal-intel-hd-graphics-opengl-does-not-work)

---

### Post by LastDino on 2014-06-24
I'm glad things worked out for you.

---

