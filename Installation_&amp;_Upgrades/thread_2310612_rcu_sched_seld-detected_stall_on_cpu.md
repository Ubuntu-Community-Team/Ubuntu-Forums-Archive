---
title: "rcu_sched seld-detected stall on cpu"
date: 2016-01-20
forum: Installation &amp; Upgrades
---

### Post by nero5 on 2016-01-20
When I try to install Ubuntu (and also tried others like Deepin, openSUSE), I boot from a live usb then it stuck at the Ubuntu splash screen. Ubuntu did not show me what error it was, but Deepin (distro based on Ubuntu) did.
Anyways, these are the errors.

This showed up before the splash screen.
```

[3.169244] [drm:i915_firmware_load_error_print [i915]] *ERROR* failed to load firmware i915/skl_dmc_ver1.bin (0)
[3.191387] [drm:intel_guc_ucode_init [i915]] *ERROR* failed to fetch GuC firmware from i915/skl_dmc_ver4.bin (error -2)
[3.193323] [drm:i915_gem_init_hw [i915]] *ERROR* failed to initialize GuC, error -5 (ignored)
[3.325212] nouveau 0000:02:00.0: priv: HUB0: 10ecc0 ffffffff (1d40822c)
[4.623245] nouveau 0000:02:00.0: DRM: Pointer to TMDS table invalid
[4.623263] nouveau 0000:02:00.0: DRM: pointer to flat panel table invalid
[4.650914] sd 2:0:0:0: [sdc] No Caching node page found
[4.650938] sd 2:0:0:0: [sdc] Assuming drive cache: write through

```


And this error appeared on Deepin splash screen and stucks there
```

32.510539] INFO: rcu_sched self-detected stall on CPU {4} (t=5251 jiffies g=355 c=354 q=64)
60.126212] NMI watchdog: BUG: soft lockup - CPU#4 stuck for 22s! [lspci:804]
88.121826] NMI watchdog: BUG: soft lockup - CPU#4 stuck for 23s! [lspci:804]
95.516666] INFO: rcu_sched self-detected stall on CPU {4} (t=21005 jiffies g=355 c=354 q=190)
120.116812] NMI watchdog: BUG: soft lockup - CPU#4 stuck for 22s! [lspci:804]
148.112426] NMI watchdog: BUG: soft lockup - CPU#4 stuck for 22s! [lspci:804]

```

The one above just repeats and stucks forever.

The system is dell inspiron 7559, i7 6700, windows 10 is on a 256 SSD, trying booting into Ubuntu live usb

Please help, I cannot find any similar post anywhere.

Thanks!

---

### Post by uniquepito on 2016-01-22
First of all, disable SecureBoot in UEFI BIOS.
Then boot from USB. After grub is loaded: Edit grub and add parameter nomodeset
Install ubuntu. After first reboot use nomodeset again. Then install nvidia binary driver and nomodesed is not needed anymore.
Anyway, everything should work just fine but sleep won't work.
Mint 17.3 works almost flawlessly with same nomodeset "hack", but you have to fight with Wi-Fi a bit to get that working (solved by update to kernel 4.4 but gpu switching does not work and runs only on nvidia gpu).
btw this post is very helpful too:
[http://askubuntu.com/questions/689380/dual-boot-on-dell-inspiron-7559-laptop](http://askubuntu.com/questions/689380/dual-boot-on-dell-inspiron-7559-laptop)

---

