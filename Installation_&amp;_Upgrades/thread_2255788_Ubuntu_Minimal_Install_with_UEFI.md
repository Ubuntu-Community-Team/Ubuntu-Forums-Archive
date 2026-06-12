---
title: "Ubuntu Minimal Install with UEFI"
date: 2014-12-07
forum: Installation &amp; Upgrades
---

### Post by primo2 on 2014-12-07
After many attempts I have a minimal install of Ubuntu from mini.iso on my netbook with UEFI. I was a little disappointed with the lack of info out there and don't have it quite how I want it so I'm looking for some input. Here's what I've done so far that worked:

[LIST=1]
[*]put the 14.10 mini.iso on my USB with ```
sudo dd bs=4m if=/path/to/mini.iso of=/dev/sdx
```
[*]pre-partitioned my disc GPT with EFI partition
[*]switched HD mode from UEFI to legacy in bios
[*]booted my USB and installed command-line
[*]at the end of install when it came to installing grub:
[LIST]
[*]changed the targeted device because the installer confused my USB with my HD
[*]set grub to install to my root partition (/dev/sda3) rather than MBR
[/LIST]

[*]Rebooted back into BIOS and switched back from legacy to UEFI
[*]used a different distro to chroot into my ubuntu install to finalize my install with some needed additions and install grub to EFI
[/LIST]

SOOOOO. On my first boot into Ubuntu I was shocked it booted up faster than my minimal installs with Arch or Debian on the same machine. Then I installed xorg, lxqt with awesome wm, and a few apps. In doing so it pulled in an INSANE number of unrelated packages as dependencies. While it is still more responsive than Lubuntu, It's not on par with the other minimal installs I've done on here. I feel like it could and should be and I'm wondering if anyone could offer some advice on:
[LIST=1]
[*]not pulling in all those unrelated packages
[*]figuring out what unneeded services or what it might be running in the background that slows things down and how to stop them
[/LIST]

I feel like there's a real need for someone with a better grip on Ubuntu to write-up a HOWTO for getting a minimal install and it should probably be included in some official docs somewhere. Please offer some suggestions.

Thanks!

---

### Post by oldfred on 2014-12-07
I would think it might be easier to create gpt flash drive, copy, not dd minimal install to flash drive. Then copy the /efi folder from the Ubuntu server to the minimal flash drive. Since syslinux is not installed, nor required, it should only boot in UEFI mode. 
Do not know if any of file structure is different. The grub.efi assumes a standard structure, so if paths are different then it either has to be recompiled or just put files where expected. 

I just looked at mini.iso and the grub.cfg has different paths for linux. It uses / where server uses /install/ for locations of kernel and initrd. And desktop uses /casper for files. 
Either grub.efi has to be compiled for those locations or files moved to correct location if grub.efi copied from that install. 

I have not installed from flash drive as I usually use ISO and just desktop, so this all needs lots of experimentation and testing.

---

### Post by sudodus on 2014-12-07
The Ubuntu mini.iso (14.04 LTS and later) boots nicely after cloning with dd (or cloning more safely with mkusb) and can install a working system in BIOS (alias CSM) mode. I have done it many times (it is part of my testing of mkusb).

But I don't think it works with UEFI. You would probably need the tips and tricks described by oldfred (including the experimentation and testing) ;-) 				

-o-

The Ubuntu family ***desktop 64-bit*** ISO files can install into both UEFI and BIOS. The most light-weight family member (alias flavour) is Lubuntu. Please tell us why you want to start from the mini.iso for an UEFI mode system, and what you want to achieve. Then we might be able to suggest some work-around :-)

---

### Post by oldfred on 2014-12-07
I had already created an ISO loopmount UEFI boot flash drive.
So I copied that structure & efi folders to an old 256MB flash drive partitioned with gpt.
Added mini.iso and grub boot stanza to boot with grub & loopmount. It booted and I went as far as the partitioner but did not want to install, so not sure it then it would correctly install grub to new system or not.
But it boots.

Not sure which grub file I copied to my flash drive originally but it is 1.4MB in /EFI/Boot so I think it was the shim from my standard install and renamed to bootx64.efi to work on a flash drive. Paths then had to match my standard install for /boot/grub with a grub.cfg (just configfile to grub.cfg in iso folder) and separate folders for fonts, & x86_64-efi.

I only tried this as sudodus had previously posted that he was able to loop mount the mini & server versions. Several years ago I tried loop mounting mini and never managed to resolve all the issues. 

Lots of names and paths are in different locations.

---

