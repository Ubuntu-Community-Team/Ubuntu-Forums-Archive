---
title: "Hardware Drivers menu not available after upgrade to 8.10"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by Lloydy on 2008-11-03
I have been suffering huge issues while upgrading to version 8.10 from Hardy, however I seem to have been able to overcome most of these, except getting my NVidia drivers to work.

I do not have the "Hardware Drivers" menu in the System > Administration and so cannot install the correct NVidia driver from there and so cannot get compiz to run.

Both the NVidia driver and the "Hardware Drivers" menu was present and working before the upgrade.

I have tried editing the menus but it is not there.

I am recent convert from Windows 6 months ago and still getting my head around Ubunbtu's quirks. Any help appreciated?

---

### Post by tuxxy on 2008-11-03
Open a terminal and see if you can run hardware drivers from there

```
jockey-gtk
```

---

### Post by Lloydy on 2008-11-03
That command does not work either 

[INDENT]"bash: jockey-gtk: command not found"[/INDENT]

Is the hardware Drivers tool something that can be installed separately?

---

