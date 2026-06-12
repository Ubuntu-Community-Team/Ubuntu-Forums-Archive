---
title: "Install appeared to succeed, but no bootloader"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by glibdud on 2012-04-27
I have a system with storage as follows:

[LIST]
[*]1 SSD: 3 partitions; 1 swap, 1 Debian stable, 1 to be used for Xubuntu
[*]1 HDD: Data
[/LIST]
I attempted to install Xubuntu 12.04 64-bit last night. The install appeared to run fine, and claimed success, but after rebooting, the Debian-installed bootloader still comes up. I had configured it to install to the MBR of the SSD (which should have replaced the existing bootloader), and ran through the installation a second time to be sure. Still nothing. Forcing it to try to boot from the HDD, it dropped me at a Grub rescue prompt. I don't know if that was pre-existing, or if that's what Xubuntu tried to install.

This was an install from CD. I ran the media check, which came back ok. Are there any known issues I may have fallen victim to?

---

### Post by glibdud on 2012-04-27
In case anyone else comes across this with a similar issue, the problem appeared to be UEFI related. I'm unclear on the technical details, since I've not worked much at all with UEFI before, but when I looked more closely at my PC's boot menu, the DVD drive showed up twice: once prefixed with UEFI, once with BIOS. I had been using UEFI because it was at the top of the list. Using the BIOS selection, the installation appears to have completed and installed the bootloader successfully.

---

### Post by oldfred on 2012-04-28
Were you booting in UEFI or BIOS mode before? That determines whether you should use UEFI or BIOS mode to install.

---

