---
title: "erased /etc/modules  !!!"
date: 2005-09-17
forum: Installation &amp; Upgrades
---

### Post by morphodone on 2005-09-17
well, i accidentally erased my /etc/modules file while adding nvidia there...
apparently i misused the echo command [-X 

anyway, the only module i know i need is nvidia...i'm wondering if there
is a way to figure out what other modules where there / need to be there

i figure i'm okay as long as i don't reboot...which shouldn't be a problem
anytime soon

i'm currently downloading the live cd - would booting into that create a usable
/etc/modules file???

please help  :???:

---

### Post by ruvil on 2005-09-17
This is my Modules file:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
snd-pcm-oss
snd-ca0106
snd-mixer-oss
nvidia




the only thing you may need to remove is the snd modules

---

### Post by morphodone on 2005-09-17
hey thanks,

at least i can copy that and use it as a possible file...
and add or subtract to it

---

### Post by bsussman on 2005-09-17
I did a little research and was unable to find out who writes this file on install or how to recreate it. We need an ubuntu builder type for that answer, I guess.

Of course it is somewhat dependent on your unique config.  Some logic had to be used to build it in the first place.

Since yours is trashed, what happens when you boot without it?  It _might_ get recreated (I doubt it but ya never know...).

---

### Post by morphodone on 2005-09-17
[QUOTE=bsussman]Since yours is trashed, what happens when you boot without it?  It _might_ get recreated (I doubt it but ya never know...).[/QUOTE]

yeah, considered that as well...eventually i'll have to reboot.  if all else fails i can reinstall.
my /home partition is seperate so no harm done

just the time it takes to reinstall and then setup time after that

---

