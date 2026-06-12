---
title: "Ubuntu 17.04 login loop, keyboard unresponsive, nvidia drivers"
date: 2017-09-16
forum: Installation &amp; Upgrades
---

### Post by brutikk on 2017-09-16
[COLOR=#111111][FONT=Ubuntu]I have looked at a few similar questions on this website, but so far none seem to solve my particular issue. I have recently compiled kernel 4.12 and have opted to use only one processor (for testing purposes). I was previously using Nvidia graphics drivers. After the kernel compilation, I was stuck in a login loop -- any time I tried to login, I would see a black screen then be taken back to the login screen.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried a fix I found on a similar question that said I should install gdm3 and use that over lightdm, so I did. Then, when booting, my keyboard is unresponsive and I see the following messages:[/FONT][/COLOR]> [INDENT][FONT=inherit]nvidia: version magic '4.12.9 SMP mod_unload ' shouuld be '4.12.9 mod_unload'
[FONT=inherit]nvidia: version magic '4.12.9 SMP mod_unload ' shouuld be '4.12.9 mod_unload'
[/FONT][FONT=inherit]kvm: disabled by bios
[/FONT][FONT=inherit]Started Run Click sysem-level hooks.
[/FONT][FONT=inherit]Created slice User Slice of gdm.
[/FONT][FONT=inherit]Started User Manager for UID 126.
[/FONT][FONT=inherit]Started Session c1 of user gdm.
[/FONT][FONT=inherit]Started User Manager for UID 126...
[/FONT][FONT=inherit]Starting Manage, Install and Generate Color Profiles...
[/FONT][FONT=inherit]Started Manage, Install and Generate Color Profiles.
[/FONT][FONT=inherit]Stopping User Manager for UID 126...[/FONT][/FONT]
[/INDENT]
[COLOR=#111111][FONT=Ubuntu]I cannot launch a terminal via ctrl + alt + f3, as my keyboard input is not recognized.


Edit:  The solution was to just boot into a previous kernel and uninstall the nvidia drivers.[/FONT][/COLOR]

---

