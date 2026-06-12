---
title: "Can't boot Ubuntu on Beelink SER5 AMD Ryzen 7 5800H"
date: 2023-06-25
forum: Installation &amp; Upgrades
---

### Post by ijsilva on 2023-06-25
[COLOR=#000000][FONT=Arial]Hello[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]I’ve just bought a SER5 Pro AMD Ryzen 7 5800H and I can’t boot Ubuntu.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I’ve tried both the ISO image provided by Beelink[/FONT][/COLOR][[COLOR=#000000][FONT=Arial] [/FONT][/COLOR][COLOR=#1155cc][FONT=Arial]_on its official website (version 20)_[/FONT][/COLOR]]("https://www.bee-link.com/cms/support/driverhardware?product_id=&keyword=&categoryId=79")[COLOR=#000000][FONT=Arial] and the last Canonical official image (version 22) available on the official Ubuntu website.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]During installation, I chose to erase disk (single boot), overwriting the Windows 11 installation.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Computer model is: SER5 PRO-E-325112EJOW64PRO-D.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Yesterday I've executed Boot-Repair. The log paste is at:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]https://pastebin.ubuntu.com/p/MWnpPhTwQj/[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Here’s what happens when installing:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]With Beelink Ubuntu ISO (version 20)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]- It installs successfully, but when trying to boot, it gets stuck on this screen:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][IMG]https://lh5.googleusercontent.com/n9BfVWZglqup8csZxA_g2J4OCEeABgOQAtQwCrT78kCYLZYNJEr603cFP87zTJk7T9zJe_D3ziTjbOx6lqjQooc2NSoMz6Vjtd_uSfTHNbrriLzd1iu0fil2O_5pb2bOtw1srDXbz7OjW9QAeoik2lM[/IMG][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- I can only load Ubuntu in recovery mode.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- After exiting recovery mode, it’s possible to load Ubuntu on normal mode, but only when exiting recovery mode.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- If I turn off the computer and turn it on again, I get the amdgpu firmware fail message and nothing happens.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- Secure Boot was already disabled as suggested by the support on Beelink official forum:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][IMG]https://lh5.googleusercontent.com/EtfgRSX28QxdMAiChUVPZu-i3DPD3aXqYNKLNRrv2-X0O_j9B-yBHfXfGVUfF80qCYm1l-0D2tBEjgSfSDWUmrjV--WXs6dtsuX4CwaD5CPSmmF_Y7iHK5ksc7Er8j9abC6x-jpUbn3vPrHHcu471fw[/IMG][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]With official Canonical Ubuntu v. 22.04 ISO[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]- Screen gets entirely black when booting from the Flash drive.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]- It’s only possible to load Ubuntu installer on safe mode.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]- After installing, it doesn’t open (it presents a black screen with no text or prompt).
- Ubuntu only when I select  Kernel 5.4 (the default 5.15 gets the black screen)

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]With official Canonical Ubuntu v. 23.04 ISO[/FONT][/COLOR]
- The same as with 22.04, except that I can't even access GRUB to select Kernel.


[COLOR=#000000][FONT=Arial]I would appreciate any clue about what could be preventing Ubuntu from running on this PC. I've already asked other Ubuntu users at work and they said that never experienced this situation.[/FONT][/COLOR]

---

### Post by c-smile on 2023-12-05
I also needed Ubuntu 20 . Downloaded it from Beelink site.

Fixed this loading problem by disabling (in BIOS setup) the following option:

Advanced > CPU Configuration -> PSS Support -> set to [Disabled]

---

