---
title: "Trying to install a GUI on an OVH Ubuntu 23.04 VPS"
date: 2023-08-14
forum: Installation &amp; Upgrades
---

### Post by olotboy on 2023-08-14
I can't seem to find a working way to do it. I've reset the VPS at least 5 time because the 5 ways I tried didn't work. I either get something with gnome but it crashes, or I try with XFCE and I get "Oh no something has gone wrong". Can someone tell me how I can do it correctly. I would like a GUI because I need to work with Laravel and Wordpress and it would be easier for me.

Here are some tutorials I tried but didn't work:
[LIST=1]
[*][https://blog.alphavps.com/how-to-install-a-gui-on-a-linux-vps/](https://blog.alphavps.com/how-to-install-a-gui-on-a-linux-vps/)
[*][https://owlhowto.com/how-to-install-xfce-on-ubuntu-23-04/](https://owlhowto.com/how-to-install-xfce-on-ubuntu-23-04/)
[*][https://www.shells.com/l/en-US/tutorial/Installing-an-XRDP-Server-on-Ubuntu-20-04#:~:text=Installing%20and%20configuring%20XFCE&text=Once%20that%20installation%20is%20finished,XRDP%20sessions%20to%20use%20XFCE4](https://www.shells.com/l/en-US/tutorial/Installing-an-XRDP-Server-on-Ubuntu-20-04#:~:text=Installing%20and%20configuring%20XFCE&text=Once%20that%20installation%20is%20finished,XRDP%20sessions%20to%20use%20XFCE4).
[*]&#8203;[https://vkttech.com/how-to-install-ubuntu-desktop-on-a-vps/](https://vkttech.com/how-to-install-ubuntu-desktop-on-a-vps/)
[/LIST]
[FONT=Calibri]
[/FONT]
[FONT=Calibri]
[/FONT]

---

### Post by MAFoElffen on 2023-08-14
Can you ssh to the VM Server Guest?

---

### Post by olotboy on 2023-08-14
Well I do use SSH to connect to my VPS in PuTTy, but other than that I don't really understand what you mean

---

### Post by MAFoElffen on 2023-08-15
So you have a connection to it...

What is the error when you try to connect from a Windows machine running RDP Guest? And how are you trying to connect to it?

---

### Post by olotboy on 2023-08-15
It worked I simply installed ubuntu-desktop instead of trying to go with a side environnement like xfce

---

### Post by MAFoElffen on 2023-08-15
I do it with Gnome Sessions...

So this is resolved. Please go to the thread Tools link in the upper right to mark this as "Solved" so other can find how you solved this.

---

