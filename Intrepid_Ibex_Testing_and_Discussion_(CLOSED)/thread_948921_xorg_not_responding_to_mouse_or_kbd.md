---
title: "xorg not responding to mouse or kbd"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ba5e on 2008-10-15
Hey, last week, after some updates (dont remember them now) to 8.10 beta, when I started up my test box it loads gdm and xorg but there is no response from my kbd or mouse.

I can drop to a VT easy, and have tried apt-get dist-upgrades etc. and even dpkg-reconfigure xserver-xorg but it has not helped (and the new xorg doesn't care so much for xorg.conf anymore). How do I troubleshoot this and find out/change my settings?

---

### Post by jfernyhough on 2008-10-15
I installed Intrepid Beta on an old Athlon XP 3200+ machine the other day and had the same problem on first boot.

I fixed it with a simple restart.

---

### Post by ba5e on 2008-10-16
> **jfernyhough said:**
> I installed Intrepid Beta on an old Athlon XP 3200+ machine the other day and had the same problem on first boot.

I fixed it with a simple restart.

I tried restarting etc but still no luck. Its frustrating as x does not respond to the keyboard or mouse....:(

---

### Post by wgrant on 2008-10-16
> **ba5e said:**
> I tried restarting etc but still no luck. Its frustrating as x does not respond to the keyboard or mouse....:(

Ensure that you have xserver-xorg-input-all installed.

---

### Post by ba5e on 2008-10-16
great, I will try this now and get back

---

### Post by ba5e on 2008-10-16
> **wgrant said:**
> Ensure that you have xserver-xorg-input-all installed.

Great! it worked, but when I logged in the screen stayed 'ubuntu brown'.

A quick apt-get update and dist-upgrade, and then a install ubuntu-desktop installed all the rest of the missing parts of my system and Its now workign great :)

---

