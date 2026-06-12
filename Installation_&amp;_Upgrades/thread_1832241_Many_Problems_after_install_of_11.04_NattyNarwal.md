---
title: "Many Problems after install of 11.04 NattyNarwal"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by nathanielw on 2011-08-24
I have just install 11.04 NattyNarwal on my GatewayGateway ML3109 next to Windows Vista. Booting from the CD or USB hung until I added "[SIZE="2"][FONT="Courier New"]irqpoll nolapic noapic acpi = off[/FONT][/SIZE]" to the install script. Upon the first reboot after installation was complete, the system hung at a blinking cursor. ctrl-alt-del ctrl-alt-F2, ctrl-alt-F1 all did nothing, holding the power button down was the only way to start over.  Booting in to system recovery mode also resulting in a permanent hang up, always after the line:
[SIZE="2"][FONT="Courier New"][ 1.653667] sd 0 :0 :0 :0 : [sda] Attached SCSI disk[/FONT][/SIZE]

I then tried viewing the normal boot process by replacing "[SIZE="2"][FONT="Courier New"]quiet splash vt.handoff=7[/FONT][/SIZE]" with "[SIZE="2"][FONT="Courier New"]nosplash --verbose text[/FONT][/SIZE]" in the grub entry. I could see the normal boot process always hanging at:
[SIZE="2"][FONT="Courier New"][ 1.620347] scsi 0 :0 :1 :0 CD-ROM HL-DT-ST RW/DVD GCC-T10N GW00 PQ : ANSI : 5[/FONT][/SIZE]
It seems as though something with the CD-ROM is causing the problem.

I was able to get the system to boot fully up by adding [FONT="Courier New"]irqpoll nolapic noapic acpi = off[/FONT] to the grub entry, however now I cannot see the battery icon when unplugged, and have no battery options in Preferences>Power Management. Also, the computer cannot shut itself off when the computer is shut down. It seems by disabling one of these power management items, like acpi, the OS cannot fully connect to the power hardware. Suggestions?

---

