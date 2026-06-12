---
title: "Problems with root and network"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by andreic on 2005-06-23
Hi,

I installed the last version of Ubuntu and discover after that the user root can't login, only the normal user can, even thought I can run the su command.

The second problem is that it doesnt show any network device on the "Network Tools - Devices" program.

Everytime I try the configure button or the "Users and Groups" button, it as me for password, and then it give the error message "Failed to run users-admin: Child terminated with 1 status".


Please help !

---

### Post by nocturn on 2005-06-23
[QUOTE=andreic]Hi,

I installed the last version of Ubuntu and discover after that the user root can't login, only the normal user can, even thought I can run the su command.
[/quote]

That is actually correct, Ubuntu does not allow root logins (hence there is no root-password).
If you want a root shell, try:
sudo su -

> 
The second problem is that it doesnt show any network device on the "Network Tools - Devices" program.


What kind of network card and machine are you using?

> 
Everytime I try the configure button or the "Users and Groups" button, it as me for password, and then it give the error message "Failed to run users-admin: Child terminated with 1 status".


This is in Gnome?
Did you use your own password?

Please help ![/QUOTE]

---

### Post by andreic on 2005-06-23
I have an IBM R51 notebook with 82541Gl Gigabit Ethernet Controller.


I work in Gnome and I tried both the root password and my password.

If I will not be able to connect to network, than I will have no option but to install another linux.

---

### Post by andreic on 2005-06-23
Do not bother anymore.  Ubuntu is history for me. I am installing Fedora.

---

### Post by nocturn on 2005-06-23
[QUOTE=andreic]Do not bother anymore.  Ubuntu is history for me. I am installing Fedora.[/QUOTE]

Good luck.

---

