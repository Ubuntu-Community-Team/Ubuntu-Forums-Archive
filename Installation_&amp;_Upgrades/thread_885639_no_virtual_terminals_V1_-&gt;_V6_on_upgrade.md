---
title: "no virtual terminals V1 -&gt; V6 on upgrade"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by russelld on 2008-08-10
upgrading from 7.04 to 7.10 (and eventually to 8.04.1)
this box (Dell Latitude D610) can't get any virtual terminals using ctrl-alt-f1 through to crtl-alt-f6,  
though it will get a the gui login and then get to the desktop.
what could be the problem?

---

### Post by Mister.Vash on 2008-08-10
Can you see if the processes are running?

ps -A | grep tty

---

### Post by russelld on 2008-08-11
thanks for that

yep definitely running,

~$ ps -A | grep tty
 6028 tty4     00:00:00 getty
 6029 tty5     00:00:00 getty
 6032 tty2     00:00:00 getty
 6033 tty3     00:00:00 getty
 6034 tty1     00:00:00 getty
 6035 tty6     00:00:00 getty
 6612 tty7     00:00:10 Xo

---

### Post by russelld on 2008-08-12
still no virtual terms in t1-t6....:confused:
really like to get this fixed...

---

### Post by russelld on 2008-08-12
found it was vga options in /boot/grub/menu.lst
removed then tty all came back!
thanks to crew on irc #ubuntu

---

