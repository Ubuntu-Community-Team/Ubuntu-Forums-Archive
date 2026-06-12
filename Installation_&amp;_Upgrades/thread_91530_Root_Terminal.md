---
title: "Root Terminal"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by roguers79 on 2005-11-17
How do I get to the root terminal in Breezy?

---

### Post by az on 2005-11-17
There are many ways.

1.  Boot into recovery mode.  You are there.

2.  Open up a terminal and run

sudo su

3.  I think there is a root terminal menu item. (Not at home ATM...)

---

### Post by roguers79 on 2005-11-17
there was a root terminal menu option in hoary hedghog. thanks

---

### Post by 23meg on 2005-11-17
Prefer [sudo]("https://wiki.ubuntu.com/RootSudo") whenever possible.

---

### Post by dcstar on 2005-11-17
[QUOTE=roguers79]How do I get to the root terminal in Breezy?[/QUOTE]
System-Login Screen Setup-Security-Allow root to login with GDM is a start.

Then open a user terminal and:

"type 'sudo passwd' in a terminal, type your user password, then type the new root password twice."

If you want to disable the root account:

sudo passwd -l root

Having root enabled is considered a security hole, because knowing the username "root" exists allows anything malicious a head-start to possibly compromise your system, but if you are reasonably confident that your system isn't that accessible, it may not be an issue.

---

