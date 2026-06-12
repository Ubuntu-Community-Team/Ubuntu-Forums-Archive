---
title: "&quot;No Boot Device Available&quot; after running Boot-Repair"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by Ahmad_Qarshi on 2013-09-03
I have Dell Inspiron with pre-installed UEFI enabled Windows 8. I created a live USB to install Ubuntu 13.04.  

After installing Ubuntu I restarted my machine but it didn't display any Boot option and started Windows 8.

Then I restarted my machine with Ubuntu Live USB and installed the Boot-Repair.

I selected the Recommended Repair option.

It displayed a message "Please disable SecureBoot in the BIOS. Then try again. Do you want to continue?". I selected Yes without disabling the SecureBoot (Sorry my fault)
Latter on it displayed message "buggy-kernal detected. Do you want to activate[Backup and rename Windows EFI files]". I selected 'Yes'.

But now I can't boot in any OS. It displays "No boot device available"

Please find below the link from Boot Repair tool.
[http://paste.ubuntu.com/6060564/](http://paste.ubuntu.com/6060564/)

P.S:- I am absolutely newbie in Ubuntu world.

---

### Post by oldfred on 2013-09-03
A lot of users with Dells seem to have worked. Have you turned off secure boot and in UEFI menu tried to boot the ubuntu entry? 

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)

This says you have Windows set as boot. BootInfo has three of these from UEFI data, but I do not know which is which. I think one is just secure boot which only shows those systems that are secure boot, the other is UEFI. Not sure if the third is CSM or just history of last boot.


> BootOrder: [COLOR=#ff0000]0001[/COLOR],2001,0004
Boot0000* UEFI Onboard LAN IPv4    ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(b8ca3ae1d39e,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot[COLOR=#ff0000]0001[/COLOR]* Windows Boot Manager    HD(1,800,fa000,b6eab9be-c43c-48d7-bd1c-94eacf51f275)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* UEFI Onboard LAN IPv6    ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(b8ca3ae1d39e,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0003* EFI USB1 PATH1 (KingstonDataTraveler G3)    ACPI(a0341d0,0)PCI(1d,0)USB(0,0)USB(2,0)HD(1,1f80,eea080,c3072e18)RC
Boot0004* [COLOR=#ff0000]Ubuntu[/COLOR]    HD(1,800,fa000,b6eab9be-c43c-48d7-bd1c-94eacf51f275)File(EFIubuntugrubx64.efi)RC
Boot2001* EFI USB Device    RC


---

