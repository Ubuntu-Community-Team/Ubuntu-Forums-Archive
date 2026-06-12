---
title: "Just installed, then updated, now a problem"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by KYhillbilly2006 on 2006-10-03
I just installed ubuntu 6.06.  I got a notice that there were 179 updates available so I went ahead and downloaded and installed.  Problem is while installing the computer froze on the capplets-data (I think that's right) update.  I shut the computer off.  Turned it back on.  Went through the log in fine but after logging in all I get is a black screen with a cursor.  I can move the cursor but there is nothing else.  

What do I do?

---

### Post by Ocxic on 2006-10-03
boot into recovery mode, form the grub boot menu, then type:
"apt-get dist-upgrade"
that should get you goin again, if not go back into recovery mode and type "dpkg-reconfigure -a"

this can also be done from a terminal (alt-ctrl-F1-8) you don't have to boot ito recovery mode.

---

### Post by KYhillbilly2006 on 2006-10-04
How do you boot to recovery mode?

---

### Post by xpod on 2006-10-04
reboot and when you see the grub screen hit the "esc" button which will take you to the grub menu....

Then just follow the instruction above....same thing happened to me when using my original live cd.

good luck

---

### Post by KYhillbilly2006 on 2006-10-04
I am totally new to ubuntu so what is the grub screen? :D

---

### Post by arkangel on 2006-10-04
it is the  fist screen you see where you can choose the SO to load 

more or less look like this 
[http://img353.imageshack.us/img353/2567/grub3boot5al.jpg](http://img353.imageshack.us/img353/2567/grub3boot5al.jpg)

so arrow down an enter in a recovery mode :)

---

