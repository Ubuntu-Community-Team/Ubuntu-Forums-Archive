---
title: "Update stalled: Bad hard drive"
date: 2013-04-17
forum: Installation &amp; Upgrades
---

### Post by BLaZuRE on 2013-04-17
So, I'm on virtually a fresh install (made some configuration changes and installed/uninstalled a few programs.

I decided to run Ubuntu update manager, but apparently one of my hard disks is bad (/dev/sde).  Update manager is in the middle of setting up a new linux kernel, but it's at the point of 
```

    run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-39 generic /boot/vmlinuz-3.2.0-39-generic
    error: cannot read from '/dev/sde'.
    error: cannot read from '/dev/sde'.
```

and it just stalled there.  It then went on to finding various images and is now stalled after finding memtest86+.  I've tried umount /dev/sde but it's already unmounted.  It still shows up on lists of devices.  Is there a way to skip ahead or stop without corrupting grub or my OS?

---

