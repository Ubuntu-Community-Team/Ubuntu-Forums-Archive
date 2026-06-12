---
title: "Intel PRO/Wireless doesn't load at startup with kernel 2.6.30-9"
date: 2009-06-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zoff_ita on 2009-06-22
Intel wirelesscard can't be loaded 'cause of:
```
[   13.331814] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   13.331818] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   13.332040] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.332055] iwl3945 0000:05:00.0: setting latency timer to 64
[   13.403324] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   13.403328] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   13.403589] iwl3945 0000:05:00.0: irq 29 for MSI/MSI-X
[   13.404730] iwl3945 0000:05:00.0: Failed to register hw (error -17)
[   13.404849] iwl3945 0000:05:00.0: PCI INT A disabled
[   13.404879] iwl3945: probe of 0000:05:00.0 failed with error -17
```

With 2.6.30-8 all works perfectly...
Someone else got this problem?
There's a fix?

This doesn't happens every boot but almost all...

Bye,
Zoff

---

### Post by MacUntu on 2009-06-22
No problems here. I can just point you to Intel's bug tracker:

[http://www.intellinuxwireless.org/bugzilla/](http://www.intellinuxwireless.org/bugzilla/)

Maybe you can try to update your driver:

Download: [http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/06/](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/06/)
How to compile: [http://linuxwireless.org/en/users/Download#Building_and_installing](http://linuxwireless.org/en/users/Download#Building_and_installing)

---

### Post by LKjell on 2009-06-22
What happen if you manually modprobe iwl3945 ?

---

### Post by zoff_ita on 2009-06-22
> **LKjell said:**
> What happen if you manually modprobe iwl3945 ?

I get the same error in dmesg...
Sometimes removing and inserting newly iwl3945 module make wlan0 available but networkmanager can't enable wireless networks...

@MacUntu
Thx for the links.
I had compiled and installed apparently succesfully updated modules but now I get this error on module load:
```
WARNING: Error inserting rfkill_backport (/lib/modules/2.6.30-9-generic/updates/net/rfkill/rfkill_backport.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cfg80211 (/lib/modules/2.6.30-9-generic/updates/net/wireless/cfg80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.30-9-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting iwlcore (/lib/modules/2.6.30-9-generic/updates/iwlcore.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl3945 (/lib/modules/2.6.30-9-generic/updates/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

I installed all dependences listed in building instructions page...
dmesg doesn't display any error...

Switching to old modules nothing happen, still the first problem...

Thanks both for help...

---

### Post by MacUntu on 2009-06-22
Strange, maybe an easier way to get a working updated driver (those compat archives are daily snapshots that sometimes just don't work) is to install the package 'linux-backports-modules-karmic'. First make sure the compat driver is properly uninstalled ('sudo modinfo iwl3945' should not show you '/lib/modules/2.6.30-9-generic/updates/...' as filename).

---

### Post by LKjell on 2009-06-22
Well it could also be the kernel. I suggest making a bug report and hope for a fix soon. Other than that enjoy 2.6.30-8

---

### Post by binbash on 2009-06-23
I have same problem.It does not load with that kernel.

---

### Post by MacUntu on 2009-06-23
Just tested a daily live CD to confirm - no problems here.

> **zoff_ita said:**
> 
I get this error on module load:
```
WARNING: Error inserting rfkill_backport (/lib/modules/2.6.30-9-generic/updates/net/rfkill/rfkill_backport.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cfg80211 (/lib/modules/2.6.30-9-generic/updates/net/wireless/cfg80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.30-9-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting iwlcore (/lib/modules/2.6.30-9-generic/updates/iwlcore.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl3945 (/lib/modules/2.6.30-9-generic/updates/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

I forgot: a reboot should work (maybe there's a better solution but that's what I always do).

Microcode is up-to-date in the package linux-firmware, so if the new driver doesn't change a thing it would be best to report this as bug.

---

### Post by syko21 on 2009-06-23
If you are manually compiling the driver it is best to first unload the modules that are affected.

```

sudo modprobe -r iwl3945
sudo modprobe -r cfg80211
sudo modprobe -r mac80211

::insert steps to compile the updated module here::

sudo modprobe iwl3945

```
As long as the modules are loaded changing them on disk won't do anything since they are read into RAM during startup.

---

### Post by MacUntu on 2009-06-23
I also got this with the modules unloaded (according to lsmod).

---

### Post by zoff_ita on 2009-07-01
2.6.30-10 kernel has solved the problem for few days...
No it's back and don't wont to leave ;D

Same error on startup and reload:
```
[   14.595935] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.595939] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   14.596365] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.596380] iwl3945 0000:05:00.0: setting latency timer to 64
[   14.665947] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   14.665951] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   14.666129] iwl3945 0000:05:00.0: irq 29 for MSI/MSI-X
[   14.666399] iwl3945 0000:05:00.0: Failed to register hw (error -17)
[   14.666591] iwl3945 0000:05:00.0: PCI INT A disabled
[   14.666608] iwl3945: probe of 0000:05:00.0 failed with error -17

```

---

