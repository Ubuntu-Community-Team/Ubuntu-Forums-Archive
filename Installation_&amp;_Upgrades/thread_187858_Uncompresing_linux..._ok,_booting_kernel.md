---
title: "Uncompresing linux... ok, booting kernel"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by mc-rpg on 2006-06-03
i have serious problems to install ubuntu 6.06, when i try to install or boot the live or check the cd for errors, it gives me the screen black with only this message: "Uncompresing linux... ok, booting kernel" no more, even a clue.

i wont deny that this is problem has been happening with the previous installation of one flight of dapper, but in the start the distro work nicely good, but after i put another ram of 512 with my previous of 256, this problems has been happening, before happens sometimes, after was definitive, and i dont know the cause especific.

debian give me:
Rebundant entry in serial pci serial_table please send the output of lspci -vv, this message (8086, 1080, 8086, 1000) send the manufacturer and name fo serial board or moem board to [email]serial-pci-inco@list.sourceforge.net[/email]

another distro (mandrake) give the follow message at the final:
pci: found irq 11 for device 0000:01:02.0
pci: sharing irq 11 with 0000:00:1d.7

it seems a problem with a pci slot, but i dont know wich is or whats happening. if someone knows tell me. this problems not seems to be for compatibility, windows boot without problems, but i think that it isn't for compatibiliyty, i think is something worse, very much worse.

PD: excuse my english, i wrote bad this time.

---

### Post by John.Michael.Kane on 2006-06-03
Can i ask if this issue has happen with just one stick of ram in the machine? if not try  reinstalling dapper with just 512meg removing the 256, and see if you get through the whole install.

---

### Post by mc-rpg on 2006-06-03
yes i do, with the 256 stick of ram too, but is the samest, i dont know, the lives of ubuntu and kubuntu dont boot too, the only live that boot is knoppix, i could install it too, but dont boot the system, it hangs when is loading all the things, something is wrong. the souspicious thing is that windows boot without problems, if is hardware problem, windows couldn't boot too.

---

### Post by CyberX on 2006-06-04
Hello
I upgradedd my old Toshiba 7010CT from breezy to dapper and after reboot it stopped the same way as yours. After some googling i found that editing grub to start linux with "acpi=off" worked, so perhaps you may try disabling ACPI in the BIOS or in the live cd options.

---

### Post by Fr@nKy on 2006-06-04
I also have this problem! I'm stuck on Windows! But this also happens to me on Mandriva One. I think Linux sucks to SATA Hard Drives and more recent hardware.

---

### Post by Fr@nKy on 2006-06-04
If there's anything I can provide so that you can help me better please tell me!

---

### Post by skelooth on 2006-06-04
i know this doesn't help but... I had that problem too after my first reboot..... I rebooted again and it thankfully went away. It appears quite random and I think it has something to do with it not recognizing the hard drive.

---

