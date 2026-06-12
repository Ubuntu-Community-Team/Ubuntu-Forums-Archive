---
title: "Maverick hanging and ati graphics driver not working"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by mdrhazy on 2010-10-12
Recently i installed Maverick on my studio 15 laptop

It frequently hangs.Nothing works and i have to restart manually
Is there any other way to restart
Why is it hanging frequently?

Also i installed ati radeon drivers using additional drver bundled with Maverick.
After installing it shows d driver to be workinng fine

But while opening Ati catalyst control centre it says d driver isnot installed
how to solve it

---

### Post by Chris_82 on 2010-10-18
> **mdrhazy said:**
> Recently i installed Maverick on my studio 15 laptop

Nothing works and i have to restart manually
Is there any other way to restart
[LIST]
[*]**hit Ctrl+Alt+F4** (or some other F# below F7).
If you see a text login screen then do login and reset your session with e.g. a gdm restart.
Or kill the hanging process if possible. You can go back to the graphical session with Ctrl+alt+F7 (or F8 ).
[*]**use the magic kernel keys**
hold down Alt and SysRq and press, **one after the other**, waiting for the commands to finish(a couple of seconds): r s e i n u b.
If the kernel is not hanging, this kills the running processes, remounts your partitions read-only, and finally reboots the system.
[/LIST]
ps: You should find that the SysRq key is your PrintScreen key.

cheers.

---

