---
title: "Problem: Install GUI for Ubuntu 8.04 Server 64-bit LTS"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by jimboy on 2010-07-14
Hi at all,

I have a problem.
After installing Ubuntu 8.04 LTS Server 64-bit on a server-machine, I want to install a gui (gnome-core & gdm)

 after *apt-get install gnome-core gdm*

I reboot the computer.

Then the computer is booting the console. But says GNOME DISPLAY MANAGER starting... [OK]

but there is no graphical user interface. That happened with KDE, GNOME and Xwindow.

i tried this on 3 different machines and that problem appears on all of them!

What can I do?

kind regards
jimboy

Dont ask, but it has to be 8.04 LTS!

---

### Post by jimboy on 2010-07-15
No ideas? :(

It's very important for me to solve this problem! =)

---

### Post by jimboy on 2010-07-16
I found a solution to solve my problem.
It's very easy to solve if you know how ;)

The solution works like that...


 apt-get remove gdm kdm 
 apt-get autoremove 
 apt-get install gnome-core gdm 
  
 /etc/init.d/gdm stop 
 apt-get remove gdm 


aptitude -> gdm suchen und installieren. 

instead of installing only gdm and gnome-core ( like apt-get ) aptitude installs also many XServer-packages.


 /etc/init.d/gdm start 


now the GUI starts and the Logon-Screen appears after pressing Ctrl-ALT-F10

---

