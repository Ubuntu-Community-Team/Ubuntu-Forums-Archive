---
title: "TTL Monitor"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by Jamiro14 on 2011-02-08
Hi. I'm trying to use a screen with a TTL connection, but until now i've been unsuccessful. I'm only able to make it work on text mode, when i change to the graphical environment it just displays a few dashes on the screen. As anyone been able to use a TTL monitor?

BTW, i'm using a AMD LX800, and in a VGA monitor i'm not able to set resolution higher than 640x480, i've tried several methods. Is there any driver i'm missing?

PS. I'm using lubuntu 10.10

---

### Post by Jamiro14 on 2011-02-08
Problem solved. I just had to change the resolution in the bios, although now it won't let me choose any ratio other than 4:3, since my monitor is 16:9 i can't see the whole screen. I've tried xrandr to add new resolution, but i can't add other than 4:3.

---

### Post by dino99 on 2011-02-08
maverick kernel directly deal with X, so be sure to rename or delete xorg.conf

---

### Post by Jamiro14 on 2011-02-08
My system doesn't has etc/X11/xorg.conf
Or at least I can't find it. Lol

---

