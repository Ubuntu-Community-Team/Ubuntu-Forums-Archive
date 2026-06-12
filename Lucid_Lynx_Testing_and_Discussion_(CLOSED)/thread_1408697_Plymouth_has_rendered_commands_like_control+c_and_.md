---
title: "Plymouth has rendered commands like control+c and alt+f2 useless"
date: 2010-02-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-02-16
If you have Plymouth installed and are running GNOME, X will restart or enter TTY2 respectively when these commands are innocently used.

---

### Post by katie-xx on 2010-02-16
[SIZE=2][COLOR=Blue]I found Plymouth was a real problem on Fedora but havent seen this one before.
Thanks ..its in my notebook for the future. Hopefully someone can explain.

Kate[/COLOR][/SIZE]

---

### Post by Ibidem on 2010-02-16
Alt+f2 was originally supposed to switch to TTY2--X has *historically* remapped that to Ctrl+Alt+F2--likewise with Alt+F1,F3,F4,F5,F6,& F7 (X virtual terminal).
Ctrl+C was a "break" command, which could kill the "child" or "parent" process.
If X is started by init & killed by user, does it restart?
It sounds like failure to reassign keys.

---

### Post by setherd on 2010-02-17
> **Starks said:**
> If you have Plymouth installed and are running GNOME, X will restart or enter TTY2 respectively when these commands are innocently used.


I have the same issue! Sometimes when just copying text using control+c it kills my session and brings me back to a login. I thought I was going crazy!

thinkpad T43 with intel 915 chipset on mine.

---

