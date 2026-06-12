---
title: "Distribution upgrade / X error"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by Blutkoete on 2011-05-06
Hello!

My girl friend made a distribution upgrade before I could warn her. Now the system boots into *tty2*, and a *startx* gives the following errors:

```

(EE) module ABI major version (8) doesn't match the server's version (10)
(EE) Failed to load module "psb" (module requirement mismatch, 0)
(EE) No drivers available.

```It's a Asus 1201HA with that GMA Intel card, so it needed some fixes with the 10.10 version already. Maybe that's the problem.

Any ideas? I plugged in a network cable and ran an update & upgrade, but that didn't solve the problem (would have been too easy).

Thank you very much,

Blutkoete

P.S.: This is the fifth time (on five different computers with three different Ubuntu versions) that I saw someone make a distribution upgrade and it never worked. Is there a trick with that? Or did I just experience a very unlucky sample of users?

---

### Post by Blutkoete on 2011-05-06
I'm following the Natty instructions for emgd [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") right now and I'll tell you if it worked.

---

### Post by Blutkoete on 2011-05-06
Hmm. That didn't help, as the system is still looking for the psb module.

```
FATAL: Module psb not found.
```

Any help will be appreciated. I tried to purge the poulsbo driver, but that didn't help (I hoped that'll remove the requirement for the psb module, but it didn't).

Thank you very much!

---

### Post by Blutkoete on 2011-05-06
Ok, I removed the PSB entry from the xorg.conf and replaced it with "vesa". Now it's booting up again, but the graphics are very slow.

Still, help is appreciated, but I was able to restore basic functionality.

---

### Post by Blutkoete on 2011-05-07
Ok, it's *kind of* working now.

So for all people with a similar problem, this here worked for me, but it might not be a clean, a good or any solution at all (maybe it was all just coincidence):


[LIST=1]
[*]When the boot process left me at *tty2*, I logged in, entered the */etc/X11/* directory and used *vi* to modify the *xorg.conf* file, changing "psb" to "vesa".
[*]I purged both the 2D- and the 3D-poulsbo-driver that I installed for Maverick Meerkat 10.10.
[*]I rebooted, with KDE now coming up correctly, only slow and with an ugly font.
[*]I followed the emgd instructions [here]("https://launchpad.net/%7Egma500/+archive/emgd").
[/LIST]
KDE looks fine now and is working at an acceptable speed. The splash screen is still ugly, even after applying all workarounds for that. But maybe that'll work in the future.

[COLOR=Red]**WARNING:**[/COLOR] [COLOR=Black]I used lots of googling, reading and try-and-error procedures to produce this solution, so I don't guarantee it's any good or won't make your screen explode.[/COLOR]

---

