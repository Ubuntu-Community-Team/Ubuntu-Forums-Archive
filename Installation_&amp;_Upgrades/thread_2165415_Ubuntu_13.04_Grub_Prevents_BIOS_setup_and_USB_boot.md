---
title: "Ubuntu 13.04 Grub Prevents BIOS setup and USB boot"
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by watinha on 2013-08-04
Hello everyone,

I have been recentlty adventuring myself with the installation of Ubuntu in an HP Pavilion Sleekbook 14.
I had successfully installed Ubuntu 12.04 in it (creating a UEFI partition with 200MB in the start of the first non-ssd device, which seemed to be required).

After that, I had tried replacing Ubuntu 12.04 with 13.04, however I forgot to "re-create" (or configure) the UEFI partition, for that installation.
As a result, any time I boot the ultrabook I get a grub command-line, which prevents me from booting pendrive Ubuntu images in order to restore the UEFI partition.
The grub command-line also shows up as I try to get into the BIOS setup screen.

I read in some places that the UEFI partition replaces the BIOS firmware, and that grub is installed in there. Then this gives me these issues.

As I try to manually load a kernel image from the grub command-line (installed in the SSD device - from the previous installation or a USB device),
grub freezes and hangs with further action, which also prevents me from initializing and booting the system from the command-line.

Can anyone help me on this one or had any similar problem?

---

### Post by watinha on 2013-08-04
Hi guys,

just managed to boot my ubuntu installation from grub command-line.
The tricky parts were the usage of the linuxefi and initrdefi commands (which were not documented in Grub documentation: [http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html](http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html)).

And identifying that the linuxefi command had to be executed with the vmlinuz-XXX-blablabla-generic.efi.sign file, instead of the vmlinuz-XXX-blablabla-generic file (as documented in other documentations). This difference is probably a result of the UEFI boot system and the EFI partition which was not updated during my last ubuntu upgrade.

After that, Ubuntu boot was perfectly run and I used the Boot-Rescue tool to fix grub issues. The Boot-Rescue tool did not fix the EFI partition,
however it did allow me to boot my machine from a pendrive, restoring the EFI partition from a live USB disk.

---

