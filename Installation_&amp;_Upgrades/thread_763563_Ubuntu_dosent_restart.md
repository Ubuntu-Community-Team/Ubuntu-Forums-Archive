---
title: "Ubuntu dosent restart"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by itsmechans on 2008-04-23
Hi All,
I have installed Ubuntu 7.10 on Laptop...its never restart...its shuts down but if i select to restart its end up with black screen and doesnt do anything...i mannually have to turn it off and restart...
Anyone have similar issue...

---

### Post by Partyboi2 on 2008-04-23
You could try this, open a terminal (Applications>Accessories>Terminal)
Then type or paste
```
gksudo gedit /etc/modules
``` Add the following line, then save:
```
 apm power_off=1
```then
```
gksudo gedit /boot/grub/menu.lst
``` (where the l is a lower case L). Find the line that start with "kernel" (under ## ## End Default Options ## section) and add this onto the end, no carriage return, all on the same line which probably wraps over:
```
 acpi=off apm=power_off
```then save. 
then
```
sudo update-grub
``` then restart.
If that does not work you could  undo the changes you made and  try adding ```
acpi=force
``` to the kernel line (where you added acpi=off apm=power_off)

---

