---
title: "Very Strange CPU Usage"
date: 2006-05-29
forum: Installation &amp; Upgrades
---

### Post by irelandshope on 2006-05-29
I have a strange problem with Dapper LTS 6.06. I have a 2.26Ghz Pentium M processor but dapper is using around 60% of the CPU when idle. I am on Kernel 2.6.15-686. The strange thing is when I run TOP in the terminal the header shows CPU usage as 60% however if you add the CPU usage in the list its less that 10%. In system monitor it is reporting as 60%.

The main Item in System Monitor seems to be Xorg at about 50% however in the list in the Terminal its about 6%, Very Strange.

If I switch back to an earlier kernel 2.6.12-9-686 it seems to be better at about 10% which still seems high for an idle machine. Anyone seen anything like this or heard of it?

---

### Post by odd parity on 2006-05-31
I'm having similar problems, top shows Xorg using about 25% CPU on my Pentium-M while idle - which is annoying, because it makes my CPU fan never spin down. I saw someone else post that the problem went away after compiling a custom kernel optimized for Pentium-M instead of the generic 686 kernel, but I ran into some compilation problems when I tried that - I'll give it a whirl again this weekend.

---

