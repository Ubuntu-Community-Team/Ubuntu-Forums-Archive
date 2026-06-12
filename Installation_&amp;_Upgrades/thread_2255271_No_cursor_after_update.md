---
title: "No cursor after update"
date: 2014-12-03
forum: Installation &amp; Upgrades
---

### Post by arehragout on 2014-12-03
Hi i need urgent help. I just did the usual software updates, but now there is no mouse cursor any more, and the touchpad does not respond.
I am on a Fujitsu laptop.
what should i do?
thanks for your help!

---

### Post by Julie_Arnold_ on 2014-12-03
I'm having the same problem, came to the forum specifically for this bug. It was an automatic update, presumably to the kernel, on around Nov. 24.

---

### Post by arehragout on 2014-12-03
It seems to be related to the new kernel 3.13.0-40, when i start with 3.13.0-39 everything works. So the question now is, how can i uninstall the 3.13.0-40 kernel? And i REALLY want to remove it!
"sudo apt-get remove --purge linux-image-3.13.0-40-generic linux-headers-3.13.0-40" does not work and gives this output:

E: Konnte Sperre /var/lib/dpkg/lock nicht bekommen - open (11: Die Ressource ist zur Zeit nicht verfügbar)
E: Sperren des Administrationsverzeichnisses (/var/lib/dpkg/) nicht möglich, wird es von einem anderen Prozess verwendet?

it's a german system, i hope any German speaking guys are around here.
thanks!

---

### Post by ajgreeny on 2014-12-03
That means that another package management application, such as software-centre, or synaptic, or update-manager. is open.

Close that and try the command again; it should then work.

---

### Post by arehragout on 2014-12-03
yes that worked together with "sudo update-grub"!! thanks for your quick help!

---

### Post by ajgreeny on 2014-12-04
Great!
Please mark the thread as **Solved** from Thread Tools menu at the top.

---

### Post by Julie_Arnold_ on 2014-12-08
Hm, didn't work for me. Cursor is still stuck at center screen.

---

