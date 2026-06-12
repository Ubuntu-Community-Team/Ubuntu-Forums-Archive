---
title: "Upgrade: gdm dies when booting but can be started manually"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by Scuzuliak on 2006-07-12
So the Dapper upgrade went pretty well for the most part, but the thing won't boot into X and I get dumped to a command line login prompt. It's something to do with the nvidia stuff because if I change the driver from "nvidia" to "nv", it will boot fine.

The strange part (to me anyway), is that when it dumps me to a command line login, if I login and kill gdm (sudo /etc/init.d/gdm stop), then login and manually start it (sudo /etc/init.d/gdm start), it starts up just fine. Plus, all the nvidia stuff works (glxinfo says "direct rendering: Yes", NVIDIA X Server Settings app runs and shows all the options, etc.)

The only thing the Xorg log tells me about the failure is this:

[INDENT][FONT="Courier New"](EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/FONT][/INDENT]

I did a diff on the Xorg log from when it fails at boot and the one from when it works, and there's no difference prior to the error message. Of course instead of the error message, it detects my card and just plain ol' works as expected.

Misc. info:

[LIST]
[*]Running the k7 kernel
[*]Card is an old GeForce 256 DDR
[*]Running the nvidia legacy drivers
[*]Have installed any updates Synaptic has listed
[*]Upgraded from Breezy to Dapper from the Update Manager
[*]Tried reinstalling the nvidia stuff, but no dice
[/LIST]

Can anyone point me in the right direction?

Thanks in advance.

- Scuz

---

### Post by fredinator on 2006-07-12
Someone else had this problem earlier, its got something to do with  the k7 kernel. Try using a normal x86 kernel and see if you still have this problem

---

### Post by Scuzuliak on 2006-07-12
Nope, no go. Exact same thing happens with the standard 386 kernel. I got excited there for a second that it would be an easy fix. :)

---

