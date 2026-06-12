---
title: "Black screen on boot after grub... OEM install works fine"
date: 2020-10-03
forum: Installation &amp; Upgrades
---

### Post by nbrett on 2020-10-03
Hi guys,

I've been having trouble installing 20.04. If I install via OEM install(for manufacturers) everything works fine(unless I go through the "prepare for shipping" process, after which I can no longer boot). But if I try to do the standard install, everything hangs up after grub screen selection. I've tried nomodeset, which works but I have terrible resolution, probably because ubuntu is using software rendering? Can I just continue using the OEM version indefinitely? I'd rather have my own account and whatnot.

Thanks!

---

### Post by CelticWarrior on 2020-10-03
Welcome.

If nomodeset works that means it's a problem with graphics drivers: Either not installed or installed but not loading. Secure Boot enabled perhaps?
Anyway, we need hardware specifications to start with something.

---

### Post by nbrett on 2020-10-03
```
~$ sudo lshw -c video
[sudo] password for oem: 
  *-display                 
       description: VGA compatible controller
       product: Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:97 memory:e0000000-efffffff memory:fcf00000-fcf3ffff ioport:e000(size=256) memory:c0000-dffff
```

I'm a linux newbie so bare with me. This is the output if I get when i run this command in OEM mode. When I run the command in a standard installation after nomodeset, it's using LLVMPipe and if I look at a log of the boot process it says something like :
[h=2]VGACON disables amdgpu kernel modesetting[/h]

---

### Post by CelticWarrior on 2020-10-03
The result with nomodeset is expected, that's what nomodeset does as a temporary workaround, never a solution.
This confirms the problem with graphics drivers after some update. Unfortunately I know almost nothing about AMD/ATI.

---

### Post by nbrett on 2020-10-06
I discovered I can log in if I blindly type in my password, after which the desktop displays fine. Any idea how to repair this so I can see login screen?

---

