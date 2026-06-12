---
title: "Ubuntu Server Edition hang on booting screen."
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by honzell on 2010-01-17
Hi,

I have tried to install Ubuntu Desktop Edition, and everything works fine. 

But when i try the Ubuntu Server Edition, using the same method of burning the iso file i downloaded from ubuntu homepage into a cd, and when i reboot my pc and the screen display the following:
[B]ISOLINUX 3.63 Debian 2008-07-15 Copyright (c) 1944-2008 H. Peter Anvin
Loading...
Initializing gfx code[/B]

and it hang there.

Do anyone know what happened? I have verified the file i download and the disc i burnt through MD5SUM. 

My Laptop spec:
Intel(R) Pentium(R) M Processor1.86GHZ
1GB Ram, 80Gb Hardisk 
OS1: Microsoft XP Home edition SP2
OS2: Ubuntu Desktop Edition

Hope someone can help. Thanks in advance

---

### Post by mörgæs on 2010-01-18
I can not explain what happened, but if you want a server, you can just add server components to the desktop install.

---

### Post by honzell on 2010-01-18
Thanks and really appreciated ur reply.

May i know how can go about doing it? Or any reference i can read up onto?

Thanks

---

### Post by mörgæs on 2010-01-18
You are welcome.

After all updates are applied, you go to System -> Administration -> Synaptic Package Manager (or something similar - I am not on Ubuntu now).

It you for example want a web server, you just search for Apache2 and select it. Synaptic will offer to install all necessary dependencies.

---

