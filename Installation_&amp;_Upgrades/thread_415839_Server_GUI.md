---
title: "Server GUI"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by xface on 2007-04-20
I have recently installed Ubuntu Server on VM Ware and i don't know how to ad a GUI to it. I've tried using "apt-get install xubuntu desktop" but that doesn't work... This was recommend to me by someone at college but they where not entirely sure if that was right.  Any help would be greatly appreciated.

.Xface.

---

### Post by taurus on 2007-04-20
```
sudo aptitude update
sudo aptitude install xubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by upthelum on 2007-04-24
I am trying to do the same thing with VMWare butafter entering the" sudo aptitude install xubuntu-desktop gdm" it doesnt work. Apparently this should work, any suggestions.

---

### Post by Swab on 2007-04-24
What message do you get?  Is networking working at all?

---

### Post by upthelum on 2007-04-25
Dont get a message as such, Firefox says cant connect to server or unable to connect. Aim just tries to connect and hangs there.

---

### Post by Swab on 2007-04-25
> **upthelum said:**
> Dont get a message as such, Firefox says cant connect to server or unable to connect. Aim just tries to connect and hangs there.

Can you open up a terminal in the VM and post the output of: ifconfig

Also in the terminal, what happens when you type: ping 4.2.2.2

---

