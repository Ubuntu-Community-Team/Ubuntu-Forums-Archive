---
title: "wakeup via PS2K/PS2M not working, unable to toggle in /proc/acpi/wakeup"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by wamanning on 2009-11-14
so i'm running 9.10 for about a week now, after upgrading from 9.04 and 8.* prior.  i'd like to enable the wakeup via my PS2K(eyboard) and PS2M(ouse).

running this @ terminal:

[INDENT][FONT="Courier New"]cat /proc/acpi/wakeup[/FONT][/INDENT]

returns this (color added by me for posting clarity):

[INDENT][FONT="Courier New"]Device	S-state	  Status   Sysfs node
...snip...
PS2K	  S3	 [COLOR="Red"]disabled[/COLOR]  pnp:00:06
PS2M	  S3	 [COLOR="Red"]disabled[/COLOR]  pnp:00:07
...snip...[/FONT][/INDENT]

which shows them as disabled.  so i type this at the terminal to toggle their s-states (i.e., enable them):

[FONT="Courier New"][INDENT]sudo echo PS2K > /proc/acpi/wakeup
sudo echo PS2M > /proc/acpi/wakeup[/INDENT][/FONT]

then i re-check their s-states with this (same as before):

[FONT="Courier New"][INDENT]cat /proc/acpi/wakeup[/INDENT][/FONT]

and these 2 devices are still disabled.

[FONT="Courier New"][INDENT]Device	S-state	  Status   Sysfs node
...snip...
PS2K	  S3	 [COLOR="Red"]disabled[/COLOR]  pnp:00:06
PS2M	  S3	 [COLOR="Red"]disabled[/COLOR]  pnp:00:07
...snip...[/INDENT][/FONT]

i've googled the interwebs and searched these forums and i've found no information beyond what i've already learned and done here.

i'd appreciate any tips!

EDIT: what makes this strange is that i *AM* able to toggle the s-state of WOL using the exact same procedure:

[INDENT][FONT="Courier New"]WOL	  S4	 [COLOR="Green"]enabled[/COLOR]   pci:0000:02:00.0[/FONT][/INDENT]

---

### Post by Shazaam on 2009-11-14
Reaching for straws here...
Do you have keyboard/mouse wakeup enabled in your pc's bios?

---

### Post by wamanning on 2009-11-15
i believe so, yes.  wakeup from stand-by used to work for this workstation on prior releases of ubuntu as well as in windows.

i'll check again, though...i have had a bunch of changes to the system w/ hard-drive configs and whatnot, so it's worth a look.

---

