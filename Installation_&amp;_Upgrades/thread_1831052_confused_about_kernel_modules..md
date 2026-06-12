---
title: "confused about kernel modules."
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by ggankhuy on 2011-08-22
ok, i learned that lspci -k will display all pci devices in hte system. -k also displays modules particular device's module is available. 

now i used rmmod to remove module of certain device. but lspci -k still displays the module. but the module name is removed from /sys/pci/drivers folder where it used to be before rmmod execution. 

so by executing rmmod i am confused whether the module is removed from system or not? Can you give clarification.

My understanding is rmmod wil completely wipe out the module from kernel whereas unload module will make it stop servicing the device. But if I execute modprobe -r <modulename>, it stil does not seem to remove it. lspci -k still displays it. thanks,

---

