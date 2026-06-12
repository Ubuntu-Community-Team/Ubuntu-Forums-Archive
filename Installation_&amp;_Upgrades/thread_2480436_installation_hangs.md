---
title: "installation hangs"
date: 2022-10-29
forum: Installation &amp; Upgrades
---

### Post by jvglynnjr on 2022-10-29
Trying to install linux on a Toshiba laptop, multiple distros have failed. 

Attempting Lubuntu 18.04 the installer gets pretty far before it hangs. I ran memcheck and it also got stuck ~48% through tests. Does this mean that my RAM is bad?

---

### Post by ne29914 on 2022-10-29
memchack is a WIN10/11 program. What are you actually doing?
Ubuntu is NOT an application that "runs under Windows".

---

### Post by #&amp;thj^% on 2022-10-29
> **ne29914 said:**
> 
Ubuntu is NOT an application that "runs under Windows".
This might be off topic, but yes it is:[https://www.omgubuntu.co.uk/how-to-install-wsl2-on-windows-10](https://www.omgubuntu.co.uk/how-to-install-wsl2-on-windows-10)

---

### Post by jvglynnjr on 2022-10-29
I have no idea what "memchack" is. When I boot up with the Lubuntu install CD, there's an initial menu, and one of the selections is a memory check. This runs for a long time, but then eventually it freezes. 

Update:  I took my 2 RAM sticks out and switched their positions, and this time the installer gave a message about "corruption in low memory" and now the installer seems to be working. It hasn't got completely through yet, but now it is going a lot further.

---

### Post by ne29914 on 2022-10-29
Where did you get the Lubuntu 18.04 installer image from? If it's from lubuntu.net, throw it away (cybersquatter site).
The correct site is lubuntu.me.
There you'll also get the current 22.04.1 ISO image.
Redo from start.

PS: Lubuntu 18.04 is totally out. From 18.10, Lubuntu uses LXQt for the graphic environment, earlier versions use LXDE.

---

### Post by ne29914 on 2022-10-29
> **1fallen said:**
> This might be off topic, but yes it is:[https://www.omgubuntu.co.uk/how-to-install-wsl2-on-windows-10](https://www.omgubuntu.co.uk/how-to-install-wsl2-on-windows-10)

Right. Super-helpful.

---

### Post by jvglynnjr on 2022-10-30
No worries, it's working now. Who knew, but rearranging the RAM did the trick!

---

