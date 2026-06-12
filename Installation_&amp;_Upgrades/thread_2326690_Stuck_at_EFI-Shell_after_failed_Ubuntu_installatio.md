---
title: "Stuck at EFI-Shell after failed Ubuntu installation"
date: 2016-06-03
forum: Installation &amp; Upgrades
---

### Post by kendama.otto on 2016-06-03
Yesterday I tried to install Ubuntu 16.04 on my Zotac ZBOX pi 320 (32-bit UEFI, 64-bit system) using [this guide]("http://liliputing.com/2014/10/run-ubuntu-zotac-zbox-pico-mini-pc-kinda.html") (and parts of [this askubuntu answer]("http://askubuntu.com/a/715843")), which has already worked for another pi 320 of mine with a debian installation. Basically, I just copied the bootia32.efi and the 32-bit GRUB from a debian multi-arch iso. At first, everything went fine. The Ubuntu live usb was showing up in the boot menu and I proceeded to the ubuntu setup, in which I chose to override my previous Windows installation and use the entire (quite limited - 32GB) internal drive. After that a warning popped up saying something like &#8220;The installer has to do some weird stuff with the UEFI. This could prevent other OSs from starting up. Do you want to proceed with the installation?&#8221;. Having done a few Ubuntu installations before and wanting to get the new system up as soon as possible, I just accepted the dialog. Sadly, the installation failed for some reason I can't really remember now (it was something about the GRUB loader not being able to be installed). 

From then on every time I plugged in a usb with an OS on it, nothing showed up in the boot menu and the computer booted straight into the EFI-Shell. I've tried several OSs (ubuntu 14, debian multi-arch, debian 32-bit, [boot-repair]("https://sourceforge.net/p/boot-repair-cd/home/Home/")) already without luck. I've also tried changing a lot of BIOS-settings and I've now reached a point where I think I'm going to do more harm than good by trying to change even more BIOS-settings. Note the USB-stick is showing up in BIOS in the &#8220;USB Configuration&#8221; section, so that doesn't seem to be the problem. The stick does, however, not show up in the Boot Options.

Below are my current Boot-BIOS-settings:
```
Setup Prompt Timeout ... 0
Bootup NumLock State ... [On]

Quiet Boot ... [Enabled]
Fast Boot ... [Disabled]

Boot Option Priorities:
Boot Option #1 ... [UEFI: Built-in EFI Shell]
```

And here are the Secure Boot Settings:
```
System Mode ... User
Secure Boot ... Inactive

Secure Boot ... [Disabled]
Secure Boot Mode ... [Standard]
```

Any ideas why this might happen or have you encountered a similar problem before? 

Thank you!

---

### Post by oldfred on 2016-06-03
I do not know the 32 bit UEFI.
But think you need the bootia32.efi anywhere there is /EFI/Boot or EFI/ubuntu in the ESP - efi system partition.

 Trying to install Ubuntu on an Acer one 10 (S1002)  32 bit
[http://ubuntuforums.org/showthread.php?t=2305272](http://ubuntuforums.org/showthread.php?t=2305272)
Instructions to install Ubuntu 14.10 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md) 


And if a Bay Trail CPU there are other issues.
      
 Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

