---
title: "hotplug subsystem freezes"
date: 2005-01-31
forum: Installation &amp; Upgrades
---

### Post by KoolDrew on 2005-01-31
I installed Ubuntu on ym system and it installed fine and needed to reboot to finish installation.  So it reboots but at the boot screen it seems to freeze when saying something about hotplug subsystem.  Is this normal?  Did it freeze or does it take a really long time?  I left it alone for about 1 min. and nothing happened.

---

### Post by martijntje on 2005-02-01
[QUOTE=KoolDrew]I installed Ubuntu on ym system and it installed fine and needed to reboot to finish installation.  So it reboots but at the boot screen it seems to freeze when saying something about hotplug subsystem.  Is this normal?  Did it freeze or does it take a really long time?  I left it alone for about 1 min. and nothing happened.[/QUOTE]
 I noticed it takes a while on my system too. You can try rebooting with all external stuff unplugged, and then selectively replugging them.

If this doesn't work, maybe you can post your HW specs. You can also try killing the proces with <Ctrl>+<C> and/or boot into safe-mode by pressing <Esc> when you get the Grub message.

---

### Post by KoolDrew on 2005-02-01
[QUOTE=martijntje]I noticed it takes a while on my system too. You can try rebooting with all external stuff unplugged, and then selectively replugging them.

If this doesn't work, maybe you can post your HW specs. You can also try killing the proces with <Ctrl>+<C> and/or boot into safe-mode by pressing <Esc> when you get the Grub message.[/QUOTE]
 Thanks for thje reply.  On my system however it does not take a lonbg time it just freezes.  I have installed Ubuntu before with the same CD on the same PC so I have no idea what is wrong, my system has also not undergone any real system changes.

Also I am not sure if this is relevent to my particular problem, but I also noticed when booting it says "creating initial device nodes..."  After that it says "KDSKBENT: Invalid argument failed to bind key 255 to value 975"

Does that have anything to do with my current problem?  Anyway to try and fix this?

---

### Post by paul.hendrick on 2005-02-01
I had a similar problem once warty was installed. The hotplug process would hang, and I'd have to alt+SysRq+e to quit it. booting with acpi disabled fixed it.
If you need acpi, upgrading the kernel seems to be the only fix.

---

### Post by KoolDrew on 2005-02-01
How do I boot with acpi disabled and what is acpi and how do I know if I need it?

Also how can I update the kernal if I cannot boot into Ubuntu?

---

### Post by martijntje on 2005-02-03
[QUOTE=KoolDrew]How do I boot with acpi disabled and what is acpi and how do I know if I need it?

Also how can I update the kernal if I cannot boot into Ubuntu?[/QUOTE]
 When you boot, you should see a grub message saying something like > Press esc within X seconds to enter menu

Press <Esc> there. In the menu there should be the option to give additional parameters to the kernel. Use it to pass the following: > acpi=off

This should allow you to boot. After this, you should be able to update the kernel.

---

