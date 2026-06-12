---
title: "Internet does not work"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by w3rt on 2008-10-22
okay so i just upgraded from hardy to intrepid, now i cannot access the internet, I am connected to the wired network but cannot access the internet with it, any ideas anyone?

---

### Post by Toe on 2008-10-22
Maybe we're affected by the same bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287450](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287450)

Or do you have different hardware?

---

### Post by w3rt on 2008-10-22
yep same hardware and i am running the same kernel so yeah i guess thats the bug

---

### Post by w3rt on 2008-10-22
just tried using an older kernel but it still does not work ....

---

### Post by w3rt on 2008-10-22
was running hardy perfectly fine, when i upgraded to intrepid i ran into a huge problem, i couldnt connect to the internet, i am using the Realtek RTL8211B network card, has anyone else had any problems with this card? i can connect to my network, i just cant connect to the internet, i thought at first it may be a dhcp problem, but i tried manual aswell as auto for dhcp and still nothing, anybody got any tips?

---

### Post by w3rt on 2008-10-22
was wrong about using a broadcom network card, the card if have is a Realtek RTL8211B

---

### Post by Toe on 2008-10-22
I just found out that my problem was caused by the installation of the backports modules and updated the bugreport accordingly.

As far as I can tell, the backported ssb module interfered with the b44 module for my ethernet.

Maybe this ssb module is causing problems with your hardware, too.

---

