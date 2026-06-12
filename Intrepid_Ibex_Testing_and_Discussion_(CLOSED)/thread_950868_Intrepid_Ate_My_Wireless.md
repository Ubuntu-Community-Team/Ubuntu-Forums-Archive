---
title: "Intrepid Ate My Wireless"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jbrown96 on 2008-10-17
I have been using Intrepid for about a week, and I really liked it. However, after some updates my wireless card is gone -- well sort of. It is an Intel 3945abg. Lspci still reports it, and it is identified as wlan0 in iwconfig. However, I can't bring it up. Ifconfig does not list it, and if I try ifconfig wlan0 up, it complains about the device not being found with an error message like SOCIOSFLAGS. I'm sure there are updates that fix it, but I'm using an the intel 1000e card, so it's disabled, meaning I have no way (that I know of) to get the updates. A few questions:
I checked my /etc/network/interfaces and it only lists> auto lo
iface lo inet loopback

Do I need to just re-add it in this file? What would be the properly syntax? Something else to get the card recognized?

OpenSUSE 11.1 Beta2 has a temporary fix (write protections that are part of the 2.6.27 kernel) and I can use my e1000 card. Do I just need to remove the module from the blacklist? How? Is is safe?

Is there any way to download the updates on another computer and transfer them via thumb drive?


Thanks for the help

---

### Post by theevilhamster on 2008-10-17
My wireless died just before i updated to 8.1, and after some general updates (and apparently a kernel update) i was advised to select the old version of the kernel in grub. ironically, 8.1 fixed mine and done the opposite to yours! i hope this helps.
good luck!

---

