---
title: "Dual boot HP Omen: Ubuntu shuts down with new battery charged, while Windows don’t"
date: 2021-02-11
forum: Installation &amp; Upgrades
---

### Post by hdaniel on 2021-02-11
[COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Hi,[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT]
[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]I have a HP Omen-15-ax009np notebook that ran dual boot managed by grub, for 3 years without issues:[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT]
[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Ubuntu 20.04 LTS[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Windows 10 Pro 64-bit Version: 19041.804[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT]
grub version: 2.04-1ubuntu26.8

[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]This week I had to replace the old battery with a brand new.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]The battery was charged overnight.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT]
[/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]With battery fully charged and plugged also to the AC adapter, the notebook was reboot in Windows.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]After login the AC adapter was unplugged. The first time it took some minutes until Windows shuts down abruptly, with no notification.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Tried again some more times. The last time Windows shutdown right as the notebook was unplugged form the AC adapter, suggesting a suddenly power failure.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Then I rebooted in Linux. The behaviour is the same. After a few seconds unplugged it shuts down. The battery was over 80% charged.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]I went back to Windows, ran HP support assistant, updated BIOS firmware and all the drivers, and let the battery discharge until it the notebook shuts down again.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]The booted in BIOS diagnostics, since there was yet some power in the battery, and ran a memory check until the computer shuts down to make sure battery is fully discharged. [/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Reboot again into BIOS and checked battery status. There was still some charge, about 40%. [/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Ran the memory test again until shutdown.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]I had to do this about 4 ou 5 times to completely discharge the battery.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]At this point the computer was not able to turn on by pressing the power button.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]With the notebook turned off I connected the power adapter until power led turn whit, indicating full charge.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]This should have done a manual battery calibration.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Booted again in windows with AC adapter plugged.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]After login I unplugged the adapter and let it run on battery. It ran for about 6 hours.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Recharge again the battery to its full, with pc turned off.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]But now, before booting, I unplugged the AC adaptor, then boot into grub and choose to start up Windows.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Windows almost started up. The computer shutdown just before the login screen. About 10 seconds after power on.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Plugged the AC adaptor again and rebooted Windows normally, then unplugged the adapter again.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]The battery this way holds the notebook for about 6 hours.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Then I tried with Linux.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Same thing if booting in battery. The notebook shuts down just before the login screen.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]But with Linux, even when booting with the AC adapter and then unplugged it, the battery does not hold many minutes. When indicator says 80% or so it shuts down. I tried several times.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Tried also to set kernel boot options in Linux to "noacpi" "acpi_osi=Linux" or "acpi_osi=Windows", but the behaviour is still the same.[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]The present state is:[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT]
[/LEFT]
[/FONT][/COLOR]
[LIST]
[*][LEFT][FONT=Calibri]cannot boot Windows or Linux from grub with battery, even if it is fully charged. The notebook shuts down right before the login screen. This is too strange, maybe a grub issue with ACPI (?).[/FONT][/LEFT]
[/LIST]

[LIST]
[*][LEFT][FONT=Calibri]If booting with AC adapter and then unplug after logging in Windows, the battery [COLOR=#000000][FONT=Calibri]supplies[/FONT][/COLOR] the computer for about 6 hours.[/FONT][/LEFT]
[/LIST]

[LIST]
[*][LEFT][FONT=Calibri]But if booting with AC adapter and then unplug after logging in Linux, the battery holds the computer for about 30 minutes only. The battery have 80% charge or more, but the computer is still shutdown.[/FONT][/LEFT]
[/LIST]
[COLOR=#000000][LEFT]
[/LEFT]
[/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Maybe this is an ACPI issue but i couldn't figure it out.

[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]Does anyone had battery issues like this?[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]I’ll appreciate any hints and suggestions,

[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT][FONT=Calibri]thanks[/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#000000][FONT=Garamond][LEFT]
[/LEFT]
[/FONT][/COLOR]

---

