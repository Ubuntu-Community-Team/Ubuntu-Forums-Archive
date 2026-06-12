---
title: "help! cant install anything"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by &lt;==hatemademe==&gt; on 2007-10-25
hi there i am a complete ubuntu noob!

i recently tried to add/remove programs to add some stuff, and i click on something to tick it and it just comes up with the mouse loading icon thing, and it wont tick, so then i tried to install updates and it came up with 

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


so first i try synaptic and it says 

An error occured

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so i go into my terminal and try: "sudo apt-get install -f" and it says

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


so i try 'dpkg --configure -a' and it says

dpkg: requested operation requires superuser privilege

if anyone could please help me??

---

### Post by Pumalite on 2007-10-25
sudo dpkg --configure -a

---

