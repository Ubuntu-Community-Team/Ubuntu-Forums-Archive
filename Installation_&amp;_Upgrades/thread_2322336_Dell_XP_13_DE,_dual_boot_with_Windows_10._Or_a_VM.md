---
title: "Dell XP 13 DE, dual boot with Windows 10. Or a VM?"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by Neil_Nand on 2016-04-27
Hello,

I recently purchased a Dell XPS 13 laptop with Ubuntu on it, I'm wanting to dual boot it with Windows 10, does any one know of any guides or have any tips on doing this? I assume just installing Windows 10 on a different partition will just end up overwriting a boot file & stop Ubuntu from booting. The only guides I can find involve installing Ubuntu on a Windows machine, not the other way around.

The reason I want to do this is to use Photoshop basically, if anyone knows of a good way to use Windows as a VM I'd be open to that. When I've tried it on VirtualBox it works but isn't quite right, not as responsive & doesn't seem to load all the Windows effects etc.

Thanks for any help,
Neil.

---

### Post by oldfred on 2016-04-27
If a new system, I would expect Ubuntu to be UEFI.
So be sure to boot Windows in UEFI boot mode to install. How you boot installer for both Windows & Ubuntu UEFI or BIOS is then how it installs.

Probably best to just make unallocated space, and let Windows create its own partitions. With UEFI/gpt it wants additional partitions, but will install its boot loader into the ESP - efi system partition. Both Windows & Ubuntu will have folders in the ESP for booting. 
It will make Windows default, but you should be able to change UEFI to boot Ubuntu. 
Also make sure Windows fast start or always on hibernation is off once installed.

As with any major change, good backups required.

---

