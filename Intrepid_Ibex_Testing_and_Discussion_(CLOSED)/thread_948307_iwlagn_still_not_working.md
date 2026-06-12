---
title: "iwlagn still not working"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by colinpat on 2008-10-15
I still cannot connect with wireless when using iwlagn.
Acer TM7720 with Pro/Wireless 4965 AG or AGN Network Corp 
Driver iwl4965 works great.
How do I load iwl4965 with kernel 2.6.27.x
Have tried wicd and it only works with driver iwl4965
iwlagn gets ip address and shows connected but can't ping anything, firefox won't load etc.

Hoping someone can help

---

### Post by Quadchris on 2008-10-15
perhaps it's a problem on you access point.

I'm using kubuntu intrepid with my laptop and (k)networkmanager it works perfectly with my accesspoint and the driver iwlagn.

If your ip is dynamically assigned by your accesspoint, this shows that your problem is on the accesspoint and not on the computer.

---

### Post by colinpat on 2008-10-15
Then why does everything work ok with the iwl4965 driver but not with the iwlagn driver.  All settings are exactly the same

---

### Post by Quadchris on 2008-10-15
I agree but if your interface is in dhcp and obtains his lease then the wifi is working right ?

Have you a logtrace from syslog ?

With log message it's easier to find the solution ;)

---

