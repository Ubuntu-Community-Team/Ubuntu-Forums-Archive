---
title: "BIOS failure handling Ubuntu after 15 years"
date: 2016-09-19
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2016-09-19
```
Mp-bios bug:8254 timer not connected to io-apic 
```

Research online and this error has fingers pointing in both directions to the hardware manufacturers and to the kernel in Ubuntu.

In the last few days I have to babysit each and every boot by nudging the mouse at a certain point in the loading process whereas formerly I just hit the ON power and turned my back on the boot process and then come back to sit down to a Ubuntu desktop.

Research online and find conflicting advice about editing the GRUB or the (??)boot confg file. None of that older workarounds seem to be in modern Ubuntu. For example sudo gedit /boot/grub/menu.lst does not point to a valid file.

Anybody have a patch advice or thought about bypassing this error when using Ubuntu 16.04 LTS?

---

### Post by oldfred on 2016-09-19
See this thread:
[https://ubuntuforums.org/showthread.php?t=2283568](https://ubuntuforums.org/showthread.php?t=2283568)

But if you have AMD:
       [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).

---

### Post by Unterseeboot_234 on 2016-09-19
Thank you for relevant, current advice. My last Ubuntu was an upgrade instead of an install from CD.

I will try a couple of hardware component swaps along with a clean hard drive install to see what is the best choice. Right now I have an AMD-64 single-core mobo and want to keep it for the firewire connection. The conflict could be happening with the nVidia graphics card. The mobo has onboard Radeon GPU. Just finding the time to do this. 

I bought a Win10 box just to run Xara (commercial version). Xara is never coming back to Linux until Visual C++ is ported over.

I still want my Ubuntu and will post my hardware choice/fix to a solve post ASAP.

---

