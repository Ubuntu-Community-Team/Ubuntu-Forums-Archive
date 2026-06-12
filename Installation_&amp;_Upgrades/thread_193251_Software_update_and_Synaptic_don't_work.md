---
title: "Software update and Synaptic don't work"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by dnccnd on 2006-06-09
I have upgraded from Breezy to 6.06. Now the software updates tells me that there are already 4 updates available. But when I click on the update icon I get the following massage:

Only one software management tool is allowed to run at the same time
Please close the other application e.g. 'aptitude' or 'Synaptic' first.

The problem is that Synaptic and Add/Remove Applications are not open! Actually I get a similar problem when I open Synaptic, while I can open Add/Remove Applications.

Any idea? Thanks!

---

### Post by John.Michael.Kane on 2006-06-09
Have you tried rebooting, and then opening synaptic [Of course you will be asked for your pass] then clik on mark all upgrades followed by apply.

---

### Post by dnccnd on 2006-06-09
Yes, I tried to reboot several times, but I get the same problem.

---

### Post by dnccnd on 2006-06-09
Actually, when I try to open Synaptic I get this message too:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

And then:

Could not upgrade the system! Fix broken packages first.

---

### Post by John.Michael.Kane on 2006-06-09
Try opening up the terminal l type this should get you going.

1) sudo sudo dpkg --configure -a
2)sudo aptitude update 
3)sudo aptitude upgrade

---

### Post by dnccnd on 2006-06-09
Thank you so much! It worked perfectly!

---

### Post by John.Michael.Kane on 2006-06-09
dnccnd your welcome. Please post if you should have any other problems.

---

