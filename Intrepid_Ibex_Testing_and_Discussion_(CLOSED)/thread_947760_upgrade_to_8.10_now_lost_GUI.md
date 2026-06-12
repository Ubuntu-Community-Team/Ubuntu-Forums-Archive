---
title: "upgrade to 8.10 now lost GUI"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by elusive_elf on 2008-10-14
It kina says it all in the title, but here's what happend.

I wanted to upgrade my laptop to the intrepid, no big deal. So I open the update manager with -f and updated it. It gave a couple of complaints that it couldn't find something on the network or something, but I just put it down to the install not being complete.

I rebooted it, and now it won't come up with the GUI.

Anyone have any thoughts?

---

### Post by tqft on 2008-10-16
First try
sudo dpkg-reconfigure xserver-xorg

then restart machine

or
 sudo /etc/init.d/gdm restart  (may be correct )

---

