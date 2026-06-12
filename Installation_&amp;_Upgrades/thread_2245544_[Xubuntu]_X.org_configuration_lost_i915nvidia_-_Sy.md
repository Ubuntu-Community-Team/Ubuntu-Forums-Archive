---
title: "[Xubuntu] X.org configuration lost i915/nvidia - SystemIO conflicts with Region"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by Sami Lehtinen on 2014-09-24
Yesterday I did install some updates for packages, including i915 libs. For some reason now my x configuration is completely gone, even if I restore it from backup, it resets back to default configuration. I checked dmesg but I don't see anything strange there. Ubuntu tried to send report about i915 package, but failed because it's not official package.

Is anyone else experiencing same problem(s)?

 - Thank you

Yes, I have four displays and two display adapters and my config is really complex. That's one of thre reasons it's harder to debug. Any great hints where I should start? Dmesg doesn't show anything interesting.

Hmm, syslog showed this. Maybe this is the reason? But it's for Nvidia module. 
```

Sep 23 21:13:25 zender kernel: [    1.384701] nvidia: module license 'NVIDIA' taints kernel.
Sep 23 21:13:25 zender kernel: [    1.384704] Disabling lock debugging due to kernel taint
Sep 23 21:13:25 zender kernel: [    1.387816] nvidia: module verification failed: signature and/or  required key missing - tainting kernel

```

---

### Post by Sami Lehtinen on 2014-09-26
I rechecked all logs, this is only indication of some problems. Is this a real problem or not?

```

[    1.404933] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    1.407757] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)

```

More data: [http://pastebin.com/n0arNLAs](http://pastebin.com/n0arNLAs)

---

### Post by Sami Lehtinen on 2014-09-29
Fresh dmesg log after re-installing Nvidia drivers. Now there's at least clear error message.

```

[    2.698382] nouveau  [     DRM] Load detected on output B
[    2.698550] nouveau  [     DRM] allocated 720x576 fb: 0x9000, bo ffff8802426c8400
[    2.698586] nouveau 0000:01:00.0: fb1: nouveaufb frame buffer device
[    2.698611] [drm] Initialized nouveau 1.1.1 20120801 for 0000:01:00.0 on minor 1
[    2.737340] nvidia: module license 'NVIDIA' taints kernel.
[    2.737342] Disabling lock debugging due to kernel taint
[    2.739748] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    2.742503] NVRM: The NVIDIA probe routine was not called for 1 device(s).
[    2.742504] NVRM: This can occur when a driver such as nouveau, rivafb,
[    2.742504] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
[    2.742504] NVRM: the NVIDIA device(s).
[    2.742506] NVRM: Try unloading the conflicting kernel module (and/or
[    2.742506] NVRM: reconfigure your kernel without the conflicting
[    2.742506] NVRM: driver(s)), then try loading the NVIDIA kernel module
[    2.742506] NVRM: again.
[    2.742507] NVRM: No NVIDIA graphics adapter probed!

```


Any ideas how to fix this? Or do I really need to rollback i915 and kernel, or am I doing something really wrong? Intel driver seems to be working with right resolution until I login, after login I guess some configuration really throws things off and resolution drops and adapter now shows tow screens on one screen, leading to situation where top and bottom menu bards actually cover only half of the screen. This is so weird.

Image: 
[IMG]http://i3.aijaa.com/b/00640/13514740.jpg?dbc364fb0ae1425b906f0108dab01565c2d49e581b8da95fcb9619802b2a3f59c483b9f1f835de5ed6d085523041631f[/IMG]

This seems to be related to the problems I'm expering: [http://askubuntu.com/questions/507302/updated-intel-display-driver-causing-errors-when-booting](http://askubuntu.com/questions/507302/updated-intel-display-driver-causing-errors-when-booting)

---

### Post by Sami Lehtinen on 2014-10-04
Solved, see:
[http://ubuntuforums.org/showthread.php?t=2220552](http://ubuntuforums.org/showthread.php?t=2220552)
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1310489](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1310489)

---

