---
title: "Can't get GRUB to load"
date: 2015-11-08
forum: Installation &amp; Upgrades
---

### Post by danwizard208 on 2015-11-08
I've been trying to get a bootable linux (not too picky about the distro atm) working on my Lenovo laptop after getting fed up with Windows 10. I *had* a set up with Grub dual booting Windows and a half installed Arch which I never used. After attempting a number of installs (manjaro next to windows, manjaro alone, ubuntu alone) I kept ending up with my hard drive unable to boot (booting from flash drives works fine). When I try, I get a black screen with some stuff ending in

```
PXE-E61: Media test failure. check cable

PXE-M0F:  Exiting PXE ROM.
```

My understanding is that the machine is failing to find a way to boot the hard drive and is defaulting to a network boot (which I'm obviously not set up for).
I have tried several permutations to just get GRUB to load but can't escape the above error.

I *think* it might have to do with UEFI/Legacy Mode. As far as I know, my machine doesn't have UEFI support, since I can't find a single reference to it in the BIOS menu, and no way to fall back to Legacy mode. However the live USB images I am using seem to report booting in EFI mode and trying to do EFI installs. 

At this point I'm at my wits end and hoping someone can ask me the right questions and give me the right advice.

Not sure if it will help, but Boot-Repair generated [this]("http://paste.ubuntu.com/13200882/").
I know you probably need more information to help me, but I'm not sure what's relevant, so just ask me what you need.

Oh, and I've got nothing left on this machine I care about, so I'm completely willing to do complete reformats or whatever is necessary. In fact, I'd prefer suggestions that just me into as clean a state as possible over solutions that try and keep something of my current configuration.

Any help will be **greatly** appreciated. Thanks.

---

### Post by oldfred on 2015-11-08
Your system is UEFI as you booted Boot-Repair in UEFI mode and it showed the UEFI boot options.

But your install is BIOS boot on a gpt partitioned drive. And you have used the advanced LVM - logical volume install. Did you really want that? It is required if you want full drive encryption.

I do not know LVM, but have some links:
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

With Secure boot on, which Boot-Repair says it may be, you can only boot in Secure UEFI mode. You should be able to turn off Secure boot and boot in UEFI mode or BIOS/CSM/Legacy mode.

Some other Lenovo, Usually UEFI/BIOS is similar across models, do they may give hints on your issues.

 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side
Lenovo S20-30 BIOS install only
[http://ubuntuforums.org/showthread.php?t=2277003](http://ubuntuforums.org/showthread.php?t=2277003)
T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by danwizard208 on 2015-11-08
Thanks for the quick reply. :)

I cannot find a setting to disable Secure Boot or to choose UEFI/Legacy when I boot my computer. All I can find options for is changing the boot order, Legacy USB (it says for stuff like mouse/keyboard) and a couple other things I can't remember. I'll try again, but I just don't know where to find those options.

As to LVM, I don't really care about it. I thought I would try it when I was a bit earlier on in this process, but I hardly need it. I'm willing to axe it.

---

### Post by danwizard208 on 2015-11-08
I can confirm that when I open up the Set Up menu with F2 on boot, there is nowhere at all a mention of UEFI or Secure Boot, and the only mention to Legacy is that Legacy USB thing I posted above.
I tried a 'reset to factory defaults', still can't boot hard drive, but this time the Live Install booted directly without showing me its GRUB menu.
Boot-info this time: [http://paste.ubuntu.com/13202679/](http://paste.ubuntu.com/13202679/).

---

### Post by oldfred on 2015-11-08
Either you posted the same one, or did reboot in UEFI mode.


> BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot maybe enabled. (maybe sec-boot, Please report this message to [email]boot.repair@gmail.com[/email])


Some systems are not as clear on what they call the three ways you can boot, UEFI with secure boot, UEFI without secure boot, or BIOS which also is not secure boot. Once secure boot is on, it often locks up many setting.

Did any of links to other Lenovos which have similar or same UEFI/BIOS help?
Some vendors may just call it Windows 8 mode meaning Secure boot, or Windows 7 mode, which could be UEFI or BIOS?
 Screen shots of secure boot settings, several models
[http://www.rodsbooks.com/efi-bootloaders/secureboot.html](http://www.rodsbooks.com/efi-bootloaders/secureboot.html)
      
 Screenshots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)

Some more older Lenovo threads:

 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212](http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

[URL="https://neosmart.net/wiki/disabling-secure-boot/"]
[/URL]

---

