---
title: "Hardware is supported, so what's wrong with plymouth?"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2010-04-16
Given that I'm on Intel graphics, why do I only get a blinking cursor followed by some terminal output on boot up? I see so many threads of people asking how to get it working on Nvidia or ATI - surely Intel should be hassle free?

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Uniwill Computer Corp Device 9917
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
    Region 1: I/O ports at 1800 [size=8]
    Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Region 3: Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```

---

### Post by DavidOC on 2010-04-16
I have the same problem and have the same graphics adapter.

---

### Post by QwUo173Hy on 2010-04-16
That's a relief. I found this bug - but according to the dev, the issue is in fact not hardware dependent:

[https://bugs.launchpad.net/plymouth/+bug/553745](https://bugs.launchpad.net/plymouth/+bug/553745)

From the other reports, it looks like this is the issue you and I share. Good to see it has a high priority :)

---

### Post by glasen on 2010-04-16
Try the following mini howto :

```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u -k all
```

First line tells the "initramfs-tools" to include Plymouth and the needed framebuffer kernel-modules (e.g. i915.ko) in the initial ramdisk-file. Second line regenerates the initial ramdisk for all installed kernels.

After a reboot Plymouth should show up directly after the loading of the kernel.

---

### Post by VMC on 2010-04-16
I have the same problem using Intel i865 video chip.
If I install Solar theme it **always** works, but the default Ubuntu logo is a crap-shoot.

---

### Post by QwUo173Hy on 2010-04-17
Glasen & VMC, thank you. I'll try both of those if it hasn't been fixed by an update at release time. For now I think I'll leave my machine unchanged so the updates can do their thing naturally and so I can keep contributing to that bug report, if needed.

---

### Post by sartic on 2010-04-17
thx, finally boot splash is working fine

---

### Post by QwUo173Hy on 2010-04-20
> **glasen said:**
> Try the following mini howto :

```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u -k all
```First line tells the "initramfs-tools" to include Plymouth and the needed framebuffer kernel-modules (e.g. i915.ko) in the initial ramdisk-file. Second line regenerates the initial ramdisk for all installed kernels.

After a reboot Plymouth should show up directly after the loading of the kernel. Glasen, thank you - that worked perfectly!

---

### Post by vredley on 2010-04-20
> **glasen said:**
> Try the following mini howto :

```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u -k all
```

First line tells the "initramfs-tools" to include Plymouth and the needed framebuffer kernel-modules (e.g. i915.ko) in the initial ramdisk-file. Second line regenerates the initial ramdisk for all installed kernels.

After a reboot Plymouth should show up directly after the loading of the kernel.

Thanks, that almost did it! The splash screen now starts, only to be interrupted by:

```

sd 2:0:0:0: [sdb] Assuming drive cache: write through
sd 2:0:0:0: [sdb] Assuming drive cache: write through
sd 2:0:0:0: [sdb] Assuming drive cache: write through

GLIB WARNING ** GLib - getpwuid_r(): failed due to unknown user id (0)
```

But things are definitely looking up. :D

---

