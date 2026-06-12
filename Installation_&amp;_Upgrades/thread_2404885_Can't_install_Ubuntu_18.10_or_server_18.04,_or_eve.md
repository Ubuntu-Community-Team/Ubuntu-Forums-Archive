---
title: "Can't install Ubuntu 18.10 or server 18.04, or even run a live USB. New build."
date: 2018-10-29
forum: Installation &amp; Upgrades
---

### Post by natrilix2 on 2018-10-29
[COLOR=#070F14][FONT=Verdana]System:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Mobo: ASRock A320M-HDV[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]CPU: AMD A8 9600 3.4GHz[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]RAM: Kingston HyperX Fury 4GBx2 DDR4 2666Mhz[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]PSU: Corsair CX450[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Issue:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Can't get any OS to install, or even run from a live USB. [/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]The system begins to boot into the OS and shows the splashscreen, but then restarts in a loop.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Have tried with Ubuntu 18.10, as well as Ubuntu Server 18.04LTS, and even using the Try Ubuntu Without Installing causes the same problem[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Have also tried Windows and Mint with no success.

I can get to the install options screen and navigate this normally, both in BIOS and UEFI [/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Will otherwise boot into the BIOS fine, and all hardware is detected normally[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]MemTest normal[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Have tried already:[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Swapping or completely removing all hard drives[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Used 2 different USB sticks, both will work on other computers[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Took HDD out of another computer and can't boot into an already successfully installed OS[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]SATA is set to AHCI[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Legacy boot tried both on and off[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Fast boot is off[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]CPU temp never greater than 36[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]-----[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]I've run out of ideas.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]The only thing that produces a different result is if I try to install Ubuntu Server form the UEFI interface, then I get a corrupted screen and no boot-loop[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Any idea? Thanks everyone.[/FONT][/COLOR]

---

### Post by natrilix2 on 2018-11-04
Solved!

After updating the BIOS to the most recent stable version I was able to install using aipc-off and nomodeset.
Still getting a [COLOR=#252C2F][FONT=&amp]*ERROR* VGACON disables amdgpu kernel modesetting message, but not causing any problems.
I assume this was a problem with the on-board Radeon graphics but it's all a bit beyond me.

Anyway, problem solved[/FONT][/COLOR]

---

