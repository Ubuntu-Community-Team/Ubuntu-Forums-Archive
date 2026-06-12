---
title: "How to install GTK2+"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by gejr on 2006-09-26
I feel like a dork. I discovered I had to install newer GTK updates to access some sweet eyecandy for Ubuntu Dapper 6.06. I've searched everywhere for this, and got caught in a rollercoaster of dependencies. Can't there be an easy way to update/install GTK2 ? I don't even know how to check which version I already have. I installed atk, cairo(which didnt really install because it needed some fontconfig AND freetype font stuff), glib, zlib+++ 

I have no idea what any of them really does, other than that I needed them for some reason. Is it really this insanely complicated to install stuff in Ubuntu, linux for human beings? Any assistance will be highly appreciated! First...which version of GTK do I have, and how can I update it if neccessary? Might be some other problem here that I cant figure out.

---

### Post by gejr on 2006-09-27
*bump* Must be somebody able to help me with this?:)

---

### Post by Jeremy23 on 2006-09-27
If you ask me, you would probably be better off installing Edgy. You wouldn't suffer from dependency hell and I honestly think it would be more stable (than manually doing it all in Dapper, that is).

I've never installed newer versions of GTK+ on my Dapper, so I can't give you a straight answer to your question, sorry.

---

### Post by gejr on 2006-09-27
Thanks..I'm generally sceptic to unfinished software, but I'll try it anyway. Havent got much to lose as it is. My current installation is crippled due to me messing around in xorg.conf without taking backups of it first. (Go me! Yay!:)

---

### Post by Jeremy23 on 2006-09-28
> **gejr said:**
> Thanks..I'm generally sceptic to unfinished software, but I'll try it anyway. Havent got much to lose as it is. My current installation is crippled due to me messing around in xorg.conf without taking backups of it first. (Go me! Yay!:)

If your xorg.conf is ever stuffed, the command ```
sudo dpkg-reconfigure xserver-xorg
``` is your friend.

---

