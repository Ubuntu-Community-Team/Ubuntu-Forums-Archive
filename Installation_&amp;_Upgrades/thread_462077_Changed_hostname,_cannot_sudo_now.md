---
title: "Changed hostname, cannot sudo now"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by JsATL on 2007-06-02
I changed the /etc/hosts file from:

192.168.1.200  LAMP1

to:

192.168.1.200  apache2.lamp1.com

now I cannot do any sudo commands, it returns the error 

"cannot gethostbyname()"

Looks like I will have to reinstall, this is a pretty bad bug in the system. Crummy foresight by the designers. 
A) How can I fix this??
B) How else can I change the computer name without damaging root access?

---

### Post by jrib on 2007-06-02
reboot and choose recovery mode from the grub menu and fix your /etc/hosts (whatever you have in /etc/hostname must point to 127.0.01)

---

### Post by JsATL on 2007-06-02
Thanks Jason, will try!

---

### Post by JsATL on 2007-06-02
Jason: Thanks, I have root BACK!

---

