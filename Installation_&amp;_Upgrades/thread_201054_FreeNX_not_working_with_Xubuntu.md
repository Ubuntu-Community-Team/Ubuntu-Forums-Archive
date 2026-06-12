---
title: "FreeNX not working with Xubuntu"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by MatBi on 2006-06-21
Hi,
i installed FreeNX from Seveas on my machine which is running Xubuntu Dapper with the [autologin hack]("http://ubuntuforums.org/archive/index.php/t-31310.html").
In the Windows NX Client configuration panel, i choosed Unix/custom, since i have no XDM/GDM.
The authentication process is successful; after that i get the red "!M" splash screen and a black window with a cross mouse pointer (which i can move around) and nothing else. After 5-6 seconds the window closes.
The log file in /var/log/nxserver.log is empty, i'm not sure what's wrong. Should i  let NX lauch a specific application? I tried with startx with no success.
Thanks in advance,
MatBi

---

### Post by Matze on 2006-06-23
Hi there,
i also use freenx on my Xubuntu/Dapper machine!
I got it working using the following:

In the Windows NX Client configuration panel, please choose
**Unix/custom**, and under "Settings..." please choose
**"Run the following command"** and type **"startxfce4"** (without the quotes!).
This works perfect for me!
Hope it helps :-)

Greets,

Matthias

---

### Post by MatBi on 2006-06-23
Thanks a lot, it works!

---

### Post by Matze on 2006-06-23
No problem! :-)

---

