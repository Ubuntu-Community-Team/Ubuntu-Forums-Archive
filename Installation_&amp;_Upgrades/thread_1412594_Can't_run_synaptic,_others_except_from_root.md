---
title: "Can't run synaptic, others except from root"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2010-02-21
Took an emachines T3265 with Win XP home and used 9.04 DVD (from Ubuntu book) to wipe out the Win XP and then install 9,04 over the entire hard drive.  I then upgraded to 9.10 using the option on update manager.  I gave my normal logon all privileges, but I can use synaptic and other functions such as changing update parameters w/o logging on as root.  If attempt same from my logon, PC crashes.

---

### Post by northrup on 2010-02-21
Do you receive errors when you use the sudo command in your normal logon (i.e. "sudo apt-get install" or "sudo synaptic")?  You can try executing Synaptic in the terminal (or using the Run dialog box, although I don't remember the keyboard shortcut right now...), but appending "sudo" to the beginning ("sudo synaptic").  It should prompt you for your password, and afterwards bring up a working Synaptic window.

---

### Post by cigtoxdoc on 2010-02-25
When I try to start a terminal session from within Gnome, I get a white book with no text.  Attempts to use synaptic, update manager from my normal user accounts locks up PC.  I restarted, logged in as root, did my updates, etc., reset my user account and ticked all boxes (e.g., can administer system) and no improvement.  I have two similar PCs also running 9.10 that work fine.

What should be my next steps?

PC is eMachines T3265.

John

---

### Post by cigtoxdoc on 2010-02-25
:KS

SOLVED, but don't know why.  If I use Failsafe GNOME, things work correctly.

Display driver is NVIDIA Driver Version: 96.43.13

John

---

