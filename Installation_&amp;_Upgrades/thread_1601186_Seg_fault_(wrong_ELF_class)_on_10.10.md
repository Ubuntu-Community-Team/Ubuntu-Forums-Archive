---
title: "Seg fault (wrong ELF class) on 10.10"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by yvsong on 2010-10-19
After upgrading to 10.10 from 64 bit 10.04, everything runs well till today. When running glxinfo, I get segmentation fault. When running skype, I get

    Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

uname shows

    Linux  2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

---

### Post by efflandt on 2010-10-20
segfault for glxinfo sounds like a video driver issue.  What video driver and version are you running if not a default driver, and what is the output of **sudo lspci -v** specifically related to your video card/chip?

Are you running a 64-bit version of skype?

Does **file /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so** show that as x86_64?  Maybe whatever that module is trying to do for skype is not x86_64:

---

### Post by yvsong on 2010-10-20
I have Intel graphics card. After removing ATI and nVidia drivers, my problem is mysteriously solved. Thanks.

---

### Post by schworak on 2010-11-14
I get the same error when trying to run Google Earth. This is the only app that seems to giving me trouble and I don't know how to fix it.


**sudo lspci -v**

01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series] (prog-if 00 [VGA controller])
    Subsystem: Dell Device 02be
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 2000 [size=256]
    Memory at fc000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at fc020000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon


**file /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so **

/usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

---

### Post by faisalsadaf on 2010-11-24
I have this exact same issue. My scenario is as follows:

- Attempting to install Bitnami native installer for Alfresco on a Ubuntu 10.10 amd64 VM (using VMWare workstation 7.x)
- ia32-libs (current version: 20090808ubuntu9) installed. Also tried an older version (20090808ubuntu4, but it didn't work. Gave a segment fault.
- Video driver details:
```
00:0f.0 VGA compatible controller: VMware SVGA II Adapter (prog-if 00 [VGA controller])
    Subsystem: VMware SVGA II Adapter
    Flags: medium devsel, IRQ 9
    I/O ports at 10d0 [size=16]
    Memory at d0000000 (32-bit, non-prefetchable) [size=128M]
    Memory at d8000000 (32-bit, non-prefetchable) [size=8M]
    [virtual] Expansion ROM at 20000000 [disabled] [size=32K]
    Capabilities: [40] Vendor Specific Information: Len=00 <?>

```im-ibus-so file info:
```

root@ubuntu:/usr/lib/gtk-2.0/2.10.0/immodules# file im-ibus.so
im-ibus.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

```Any other suggestions on how to resolve this?

Thanks

---

