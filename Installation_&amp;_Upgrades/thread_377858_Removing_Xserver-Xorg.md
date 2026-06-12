---
title: "Removing Xserver-Xorg"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by gfca on 2007-03-06
Hi people!

I have a little network (4 PC's) at home to do some experiences in networking/samba. They have Ubuntu Edgy with X... but now... i want to remove Xorg.

I thought that i did that when run "apt-get remove xserver-xorg" but i was wrong (I think).

I wanna do a dist-upgrade do Feisty but this will install Xorg and I don't want that.

Can someone help me?

Thank'a a lot!!!
Gonçalo Almeida

---

### Post by bulldog on 2007-03-06
Can you explain why you don't want the X-server installed?

You need the xorg.conf because it sets up your hardware,without the X-server I don't think you have the capability to login to your desktop.
If you want a server install without the graphical interface,just remove the ubuntu desktop.

---

### Post by zvacet on 2007-03-06
Do you mean you don´t want desktop anymore and you want work from terminal?If that is the case then
```
apt-get remove ubuntu-desktop
```

---

### Post by gfca on 2007-03-06
Because I only wanna console! 

I thought that Xorg.conf only matters to window system, not to console! That's why i removed the xserver-xorg.
But if you say that i will install again...

Thanks a lot!!!

---

