---
title: "Ubuntu installer hangs at logo"
date: 2015-04-29
forum: Installation &amp; Upgrades
---

### Post by Tyler_Slabinski on 2015-04-29
I'm trying to install Kubuntu 15.04 on a Dell Precision 7910. However, the installer hangs a few seconds after the logo appears. This occurs on Ubuntu 15.04 as well.

Removing the **quiet splash** parameters on grub shows the following at the end:

```

[17.616442] systemd-journald[1228]: Received request to flush runtime journal from PID 1
[ OK ] Started Load Kernel Modules.
[ OK ] Started udev Kernel Device Manager.
systemd-modules-load.server
    Mounting FUSE Control File System...
systemd-udevd.service
    Starting Apply Kernel Variables...
[ OK ] Mounted FUSE Control File System.
sys-fs-fuse-connections.mount
[ OK ] Started Flush Journal to Persistent Storage.
systemd-journal-flush.service
[ OK ] Started Apply Kernel Variables.
systemd-sysctl.service
[ OK ] Started Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling.
lvm2-monitor.service
[ OK ] Created slice system-ifup.slice
```

At that point it hangs.

I have tried the **nomodeset** parameter, but that does not seem to work. While the graphics card is Nvidia, I suspect that isn't the issue.

Here is a link to the hardware: [URL="http://www.ubuntu.com/certification/hardware/201405-15066/"]http://www.ubuntu.com/certification/hardware/201405-15066/
[/URL]
EDIT: Seems that the 14.04 installer will boot up fine. I will try installing it and upgrading to 15.04 afterwards, but I'd like to figure out why the 15.04 installer would not boot.

---

