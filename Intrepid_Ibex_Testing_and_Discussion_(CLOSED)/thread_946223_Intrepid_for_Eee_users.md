---
title: "Intrepid for Eee users?"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Tommy Rydling on 2008-10-13
Hi all,

I have an Eee PC 901 and have used Ubuntu 8.04 for a while. Generally I am very pleased.

I also tried installing the beta of Ubuntu 8.10 (Intrepid), but lost my wifi functionality, like so many other users.

My question is:
Does anybody know if and when there will be an Eee-tailored version of Intrepid (like they have with version 8.04)? Also, does anybody know whether the wifi functionality will be stable once Intrepid is out of beta?

I am really looking forward to losing the whole xorg.conf editing problem when upgrading to Inptrepid, but not if it means editing another file to get wifi working.

Thanks for any input.

---

### Post by surfed on 2008-10-27
> **Tommy Rydling said:**
> Hi all,

I have an Eee PC 901 and have used Ubuntu 8.04 for a while. Generally I am very pleased.

I also tried installing the beta of Ubuntu 8.10 (Intrepid), but lost my wifi functionality, like so many other users.

My question is:
Does anybody know if and when there will be an Eee-tailored version of Intrepid (like they have with version 8.04)? Also, does anybody know whether the wifi functionality will be stable once Intrepid is out of beta?

I am really looking forward to losing the whole xorg.conf editing problem when upgrading to Inptrepid, but not if it means editing another file to get wifi working.

Thanks for any input.

You can install the custom kernel from array.org for an eee specific kernel for intrepid. The lean version is specially nice as it strips all hardware support from the kernel that is not eee specific and builds most relative modules directly into the kernel, making it leaner and faster at boot. Warning: You will loose wireless until you install the eee specific kernel.

---

### Post by jfernyhough on 2008-10-27
The wireless works with the standard kernel, it's just not obvious.

Either disable (deactivate) the driver in Hardware Drivers (jockey) or add "blacklist ath_pci" to /etc/modprobe.d/blacklist (and reboot, obviously).

At least, this works on my 701; I assume it's the same for the others.

Oh, also try adding elevator=deadline to the boot option in GRUB (after quiet splash) - it speeds up my 701 (and Acer) no end.

---

### Post by surfed on 2008-10-27
> **jfernyhough said:**
> The wireless works with the standard kernel, it's just not obvious.

Either disable (deactivate) the driver in Hardware Drivers (jockey) or add "blacklist ath_pci" to /etc/modprobe.d/blacklist (and reboot, obviously).

At least, this works on my 701; I assume it's the same for the others.

Oh, also try adding elevator=deadline to the boot option in GRUB (after quiet splash) - it speeds up my 701 (and Acer) no end.

post 900 models, 901 and 1000 use a diffeerent wireless card (only the 801.11n versions?)
Its a RaLink using the module rta2860sta

---

