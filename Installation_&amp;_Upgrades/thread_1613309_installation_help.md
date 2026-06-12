---
title: "installation help"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by seth_rutland01 on 2010-11-04
hi all i am new to ubuntu and trying to install on acer extensa 5235 i managed to install using wubi and then booted into ubuntu from the grub. it froze after a load of text (last line was kernel_thread_helper) shutdown and rebooted pressed esc and chose acpi workaround and it finished the install but now when i boot it comes up with the same text as before and freezes at the kernel_thread_helper. 

if anyone could help it would be greatly appreciated.

---

### Post by bcbc on 2010-11-04
You have to apply the workarounds each time you boot - until you do something to resolve the issue. So hit 'e' on the first grub menu entry and go to where it says 'quiet splash' and add the workaround. E.g. 'noacpi quiet splash' or whatever the workaround was. Then CTRL+X to boot.

If you can solve the problem by installing custom drivers then do that (System, Administration, Hardware Drivers) - otherwise you can make the workaround permanent by editing /etc/default/grub and running 'sudo update-grub'

To add workarounds to the startup options permanently:
Go to a terminal CTRL-ALT-t
Edit file: "gksudo gedit /etc/default/grub"
Change boot options from:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to: (e.g.)
GRUB_CMDLINE_LINUX_DEFAULT="noacpi quiet splash"  
Save, exit, 
Update grub menu: "sudo update-grub"


EDIT: I just checked and for acpi_workarounds, it looks like wubi uses the following:
acpi=off noapic nolapic

---

