---
title: "Accidently Disabled ATI Drivers in Feisty"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by duddy on 2007-04-20
How do I re-enable them? When I boot Feisty, it tells me that my X is messed up and that I need to fix it. :P

I need to re-enable the ATI driver from the terminal. I'm using a Dell laptop with an ATI 9600 Pro.

---

### Post by jaimz on 2007-04-20
sudo dpkg-reconfigure xserver-xorg

I believe I typed it right

anywho, just select ATI (or fglrx if you're using them)

---

### Post by duddy on 2007-04-20
You mean I don't have to do a clean install or anything?

There's no way it could be that easy!

OK, I'll give it a try and report back.

---

### Post by jaimz on 2007-04-20
edit - I'm sure you'll have to boot in recovery mode of if X doesn't load and you can still log on, you can just do it through there

---

