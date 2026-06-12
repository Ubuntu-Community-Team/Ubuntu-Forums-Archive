---
title: "[SOLVED] Firefox opens in Work Offline mode"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bwallum on 2008-10-08
Hi

I'm sure I've read about this before but can't find it. Firefox always opens in Work Offline mode even when closed with the 'Work Offline' check box empty.

How do I change the default to open on line?

Rgds
Bob

---

### Post by Mr Fredrick on 2008-10-08
Does the following help?

[http://ubuntuforums.org/showthread.php?t=940364&highlight=Mr+Fred]("http://ubuntuforums.org/showthread.php?t=940364&highlight=Mr+Fred")

---

### Post by ellalan on 2008-10-08
Hi
Go to Terminal and type:
gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf

Then you find the lines(3or4) <allow send-interface......
change "allow" to "deny" then save and close.

This is what I did and HTH.

---

### Post by bwallum on 2008-10-08
That worked, I used the 

> I had this same problem, I had to edit /etc/NetworkManager/nm-system-settings.conf and changed the line under [ifupdown] to managed=true

solution.

Thanks all!

---

