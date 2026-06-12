---
title: "problems with uefi dual boot windows 8 and ubuntu 13.04"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by Jon_Royal_Ouverson on 2013-08-12
I can usually work out these problems through reading forums but I am completely stuck. I have installed ubuntu 13.04 along side windows 8 with uefi using legacy mode during the install (only way to get the live cd to boot). I originally created a partition using windows to install ubuntu on. During the install, the ubuntu installer did not recognize another operating system (windows 8) so I used the "something else" option and installed into the free partition that I had previously created. When the install finished, I could boot into ubuntu using only legacy mode and could boot into windows with uefi enabled. There was no grub which is understandable since the installer didn't see a need for grub. I then booted into ubuntu and ran boot-repair thinking it would install a grub and everything would be fine. Since then I have been able to load windoze from the grub but ubuntu will not boot (it hangs on a purple screen). Trying to boot ubuntu in recovery mode shows that it hangs on "loading initial ramdisk". I have a boot-repair file if anyone is interested in helping me with this. 
[http://paste.ubuntu.com/5978834/](http://paste.ubuntu.com/5978834/)

Thanks in advance,

---

### Post by oldfred on 2013-08-13
It sounds like you may be booting ok, but having video issues. You may need nomodeset, but many new systems seem to also need nomodeset plus other boot parameters.

What model computer and what video chip.

At grub menu press e, scroll to linux line and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)


 Some systems need these boot parameters
ACPI=Off nomodeset 
pci=nomsi noapic
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w

---

