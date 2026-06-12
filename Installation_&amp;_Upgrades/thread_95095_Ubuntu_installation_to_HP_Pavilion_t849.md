---
title: "Ubuntu installation to HP Pavilion t849"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by tim67 on 2005-11-25
hi, 

to anyone trying to install to HPPavilion t489 :

I tried to install ubuntu to HP Pavilion t849 ( AMD Athlon 64 CPU )
with no success from DVD . The installation would not start or stopped in 
"disabling IRQ #10" just after USB detection

I tried different options, and got the installation to work with
the following options:

boot: linux noapic nolapic pci=noapci acpi=off debian-installer/probe/usb=false

i tried boot options befor installation with live cd ( cd-rw ) before 
i installed from dvd-rw

-timo

---

