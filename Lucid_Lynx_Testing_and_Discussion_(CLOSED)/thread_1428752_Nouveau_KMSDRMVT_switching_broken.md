---
title: "Nouveau KMS/DRM/VT switching broken?"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2010-03-13
Just updated to the latest and greatest lucid x86_64 bits (no PPAs) to get some plymouth/nouveau/theme updates and fixes but it looks like VT switching is broken for the new nouveau bits merged into the kernel.

The call-for-nouveau-testing feedback wiki page also has a few entries indicating the same: [https://wiki.ubuntu.com/X/Testing/NouveauEvaluation](https://wiki.ubuntu.com/X/Testing/NouveauEvaluation)

Something I see in the logs that might be a NULL pointer dereference/corruption issue?

```

Mar 13 17:28:14 thunderbird kernel: [   10.078320] [drm] nouveau 0000:01:00.0: PFIFO_INTR 0x00000010 - Ch 1
Mar 13 17:28:14 thunderbird kernel: [   10.078328] [drm] no 0x00000010 - Ch 1
Mar 13 17:28:14 thunderbird kernel: [   10.080774] [drm] no 0x0000 0x00000010 - Ch 1

```

I can avoid the problem by adding "nouveau.modeset=0" to my kernel boot options which lets me log into X/KDE but I cant switch VT to get console nor can I see plymouth. I uninstalled plymouth and plymouth-x11 packages but still get the problem so its not likely to do with plymouth just plain DRM/KMS/VT issue with the nouveau code merged into the kernel.

Some package/module info:

```


vishal@thunderbird:/var/log$ aptitude show linux        
Package: linux
New: yes
State: not installed
Version: 2.6.32.16.17
Priority: optional
Section: metapackages
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 32.8k
Depends: linux-image (= 2.6.32.16.17)
Provided by: type-handling
Description: Generic complete Linux kernel.
 This package will always depend on the latest generic complete Linux kernel available.

vishal@thunderbird:/var/log$ aptitude show plymouth
Package: plymouth
State: installed
Automatically installed: no
Version: 0.8.0~-14
Priority: standard
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1602k
Depends: libc6 (>= 2.8), libcairo2 (>= 1.2.4), libdrm-intel1 (>= 2.4.9), libdrm-nouveau1
(>= 2.4.11-1ubuntu1~), libdrm-radeon1 (>= 2.4.17), libdrm2 (>= 2.4.3), libglib2.0-0
         (>= 2.12.0), libpango1.0-0 (>= 1.14.0), libplymouth2 (= 0.8.0~-14), upstart-job,
udev (>= 149-2), mountall (>= 2.0)
Conflicts: usplash
Breaks: gdm (< 2.29.1-0ubuntu4)
Description: graphical boot animation and logger - main package
 Plymouth is an application that runs very early in the boot process
(even before the root filesystem is mounted!) that provides a graphical
boot animation while the boot process happens in the background.

vishal@thunderbird:/var/log$ lsmod | grep nou
nouveau               514275  0 
ttm                    60847  1 nouveau
drm_kms_helper         30742  1 nouveau
drm                   198930  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau


```

I'm trying to report this by running "ubuntu-bug linux" but at the end of uploading the report it aborts saying "cannot access bug information page check your internet connection" - oh the hoops we have to jump through :lolflag:

So I am trying to manually open a bug report but looks like the place to do it is hidden away now if not entirely disabled.

NOTE that I am running latest lucid (kubuntu - which looks like it has package dependency issues in the archives) x86_64 and booting off karmic's grub not lucid's grub2.

Is anyone else facing this problem and have a bug report I can confirm and attach info to?

---

### Post by vishalrao on 2010-03-13
Oh by the way, I've got an 8800 GT:

```

vishal@thunderbird:/var/log$ dmesg | grep nou
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-16-generic root=/dev/sda5 quiet splash libata.force=noncq nouveau.modeset=0
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-16-generic root=/dev/sda5 quiet splash libata.force=noncq nouveau.modeset=0
[    6.852947] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x092880a2)
[    6.855063] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0

```

---

### Post by RAOF on 2010-03-15
It's worth noting that &#8220;nomodeset&#8221; will actually disable the nouveau drivers; the kernel driver will load, but the X driver doesn't have any modesetting code anymore and relies solely on KMS.

X should fall back cleanly to nv or vesa, though.

---

