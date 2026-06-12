---
title: "Messed Up Installation"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by mrgoodbytes21 on 2013-06-23
I recently got a Lenovo laptop that came with Windows 8. I installed Ubuntu 13.04 via LiveUSB alongside Windows 8, but when I select the Windows 8 boot option from the grub menu, it says invalid EFI file and cannot find "drivemap." I'm fairly comfortable using Ubuntu, so I would like to delete the Windows 8 partition. Would that do any damage to my Ubuntu partition or can I just delete it using the LiveUSB?

Also, after this is done, could I use VirtualBox to use Windows 7 on Ubuntu? Thanks.

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]mrgoodbytes21; Hi !

I am not at all smart on Windows ... But, I have seen where with dual booting with Windows the install must be done with UEFI enabled in bios to accommodate Windows.
Now again I know nothing anymore about Windows but, what might have happened in this instance is that ubuntu has overwritten Window's boot code..maybe ... and if you want to keep Windows, you might have to repair that boot sector with Windows repair utility.

What I suggest to try first is (re-)install ubuntu ..making sure bios is set for UEFI booting.... ubuntu will gladly accommodate and in the install procedure chainload Windows onto the ubuntu bootloader (grub) - if Windows' boot code still exist.

In regards to VM ...yes ! but ya got to install Windows from OEM install disk.
[/COLOR][INDENT=2][COLOR=#000000]
oh ! The complexities of modern technologies  [/COLOR][/INDENT]

---

