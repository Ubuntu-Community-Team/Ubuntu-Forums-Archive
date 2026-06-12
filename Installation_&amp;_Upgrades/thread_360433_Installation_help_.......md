---
title: "Installation help ......"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by saisrikar on 2007-02-13
hey ...

when i boot from a Ubuntu Desktop Live CD ...
i Get the Ubuntu Splash screen ...
and then , Loaded drives has a "OK" besides it ...
then it hangs at Mounting File System, 
then a Screen shows ...
"PCI: Failed to allocate mem resource #6: 2000 @ 90000000 for 0000:01:00.0" and my system also hangs at the mounting root file system step

what is wrong , how can i fix this error , plz help ...
im running a 
Core2duo 1.6Ghz,
1Gb ram 
Intel DG965RY Mobo , with PCI-E Nvidia 7600GS 

Any help will be Appreciated

---

### Post by Kateikyoushi on 2007-02-13
I am not sure exactly what is related but you could try to use these options at boot.

Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

