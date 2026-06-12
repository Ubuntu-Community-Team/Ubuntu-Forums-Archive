---
title: "Keyboard and mouse unresponsive in KDM after logout"
date: 2008-07-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bachstelze on 2008-07-26
Okay, so I have two systems running II, with KDM as default login greeter. The first login works fine, but after I logout, KDM doesn't respond to keyboard pressing or mouse movements anymore, and the only way I can log back in is to switch to a VT with Ctrl+Alt+F2 and restart it with [FONT="Courier New"]sudo /etc/init.d/kdm restart[/FONT].

Anyone else having the same issue?

---

### Post by rootkit on 2008-08-25
I confirm this bug with latest 4.1.0-0ubuntu8

---

### Post by stmiller on 2008-08-29
I have this problem, but when kdm starts. My trackpad thing (EeePC) works OK, but keyboard on EeePC does not respond when kdm starts. I have to restart X with menu option (picked via trackpad) then keyboard works ok.

Xorg logs look ok but I'll check again to see if anything is funny.

This is an EeePC 701 using Intel GMA 950.

---

