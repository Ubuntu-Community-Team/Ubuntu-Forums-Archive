---
title: "Unable to install Kubuntu 14.04.1 on UEFI system"
date: 2015-02-17
forum: Installation &amp; Upgrades
---

### Post by americast on 2015-02-17
Hi all,
  I am trying to install Kubuntu 14.04.1 LTS as the second operating system on an HP Probook (powered by intel core i3). I have disabled secureboot and fastboot from UEFI/BIOS settings. I had created a live image of 'kubuntu-14.04.1-desktop-i386.iso' on a pendrive. The installation went fine. But, the system does not boot into grub. It only boots Windows 8.1 (which came preinstalled).
  I had applied the command ```
bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
``` in command prompt but it bore no fruit. I had created the live usb using Universal USB installer. Any help would be appreciated.

Gramercy...

---

### Post by sudodus on 2015-02-17
You need the 64-bit version (amd64) to run in UEFI mode. See the following links for more details:

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295"). 
If  you want to boot in UEFI mode and install your Ubuntu flavour alongside  Windows, you should use a 64-bit ISO file, for example 
[B]
kubuntu-14.04.1-desktop-amd64.iso[/B]

---

