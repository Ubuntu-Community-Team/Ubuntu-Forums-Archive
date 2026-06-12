---
title: "Ubuntu Booting Issues and Questions About ACPI"
date: 2018-12-16
forum: Installation &amp; Upgrades
---

### Post by dwygant2 on 2018-12-16
Hi,

Over the weekend I've been attempting to dual boot Ubuntu 18.04 with my already present Windows 10 OS.
I believe I have completed all of the proper procedures in achieving this task. However, I have been running into the issue of Ubuntu failing to boot nearly 100% of the time.

Any attempt results in lines of text resembling the following:
 [INDENT][COLOR=#000000][FONT=Ubuntubeta][1.084001] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover t[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][1.084085] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover t[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][1.142468] Couldn't get size: 0xB000000000000000e[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][1.820866] nouveau 0000:02:00.0: bus: MMIO read of 00000000 FAULT at 022554[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][ IBUS ][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][1.827491] nouveau 0000:02:00.0: bus: MMIO read of 00000000 FAULT at 10ac08[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][ IBUS ][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]/dev/sdb3: recovering journal[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]/dev/sdb3: clean, 177875/18423808 files, 3210932/73665792 blocks[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][36.044004] watchdog: BUG: soft lockup - CPU#2 stuck for 22s! [plymouthd:352]
[/FONT][/COLOR][/INDENT]

Now, in all of my online searching, I've noticed a lot of suggestions regarding the "acpi=off" parameter.
Today, I attempted to use this parameter temporarily in the boot. Aside from relatively lengthy boot, Ubuntu appeared to boot fine!

I've attempted to do a little more research into what this option means and I have not been able to really understand exactly what is going on.

My question is this:
Should I make this a permanent parameter in the Ubuntu boot?
Can this cause issues with the OS or computer in the future?

---

### Post by CatKiller on 2018-12-16
The issue is that because the specifications are loose, BIOS writers do their own thing. They only check that it works with whichever version of Windows is current.

That parameter tells Linux to simply ignore what the BIOS is saying, and try to work things out itself.

You can fiddle around with the settings in the BIOS to try to disable whichever part is causing issues, or selectively apply kernel parameters to see where the problem is, if you're interested and can be bothered. There's no harm, as such, in not using ACPI, so go with it if it's working for you.

---

