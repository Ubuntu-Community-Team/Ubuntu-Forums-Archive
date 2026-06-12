---
title: "Win 10(64) and Ubuntu 14.04 Dual Boot Issue"
date: 2015-11-19
forum: Installation &amp; Upgrades
---

### Post by Kyle_Hegle on 2015-11-19
[COLOR=#000000][FONT=Arial]Trying to install Ubuntu 14.04.3 (64-bit) to a Toshiba Satellite laptop (Core 2 Duo 2.26Ghz w/4Gb RAM).  I am trying to dual boot with Windows 10 (64-bit) on non-UEFI system.  I have a 320Gb HDD with the following partitions:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][IMG]https://lh6.googleusercontent.com/OPz4eo-mbG6XbYC6jYP-fC8Qeb7tMv1fHO3Nx30eOb7L0NV4cz5q9i4WX0sXERyiF_YroR7R2i1XdPycZs6L1_sVbOOW18fEfgGAU5SuI9nAXbJjVOuhzx5LoPyJHTI7V7MpRaqg[/IMG][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I have tried to partition the unallocated space in the Ubuntu installer and have gotten Ubuntu installed multiple times, but have been unable to boot to it.  I do not even get an option to boot to it.  Can anyone help?  Thanks in advance.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-11-19
Welcome. A non-UEFI system with Win10? In that case, what is the 500mb system reserved partition in your screenshot? 

Anyway, what do you have on those partitions? Windows is on C: I take it and you want to install Ubuntu on to the 132Gb unallocated space? 

Could you please boot from the Ubuntu install media, DVD or USB, 'Try Ubuntu', once at a desktop launch Gparted and give us a screenshot from that?

PS: There is no Ubuntu installed on that drive so you wouldn't be able to boot to it. Please detail the exact procedure you are using to create the install media and install. Thanks.

---

### Post by oldfred on 2015-11-19
Even in BIOS mode with Windows 8 or 10 you need to turn fast start up off.

       Fast Startup off/hibernation - Windows 8 or 10 UEFI or BIOS boot.
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Are you installing grub to MBR? Or sda not to a partition like sda5?

Windows normally uses two partitions, system reserved is usually its Boot partition.

---

