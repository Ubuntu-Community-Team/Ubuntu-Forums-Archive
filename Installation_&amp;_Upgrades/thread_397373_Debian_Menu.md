---
title: "Debian Menu"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by Tuxaby on 2007-03-30
Installed Debian Menu and it didn't work.   Started looking and found these. I removed and reinstalled  the package and still have the problem.  How do I fix?   Lee

---

### Post by pradeepadapa on 2007-03-30
if u wanna install debian menu, first u hav to install Automatix2 , from that go the micellanious menu nd there select the debian menu nd then click start, it will download and then installs automatically,

nw u can see the debian menu in the Applications menubar.

---

### Post by Tuxaby on 2007-03-30
Found no  Automatix2 in the package list or on the web with a package search.  Search results : "Can't find that package, at least not in that distribution and on that architecture". I'm running Ubunyu 6.06 LTS.   Once I am sure this is the Linux I want to stick with I will upgrade to the latest version.   Lee

---

### Post by rocknrolf77 on 2007-03-30
[www.getautomatix.com](www.getautomatix.com)  :)

---

### Post by Skidpad on 2007-03-30
Automatix isn't necessary to get the Debian menu.  The problem is when you install Debian, you must also update your menus.  

Looking back through my terminal history, here is the code I used to install the menu packages.  (I originally had the same problem as Tuxaby)

**Code**
sudo apt-get install menu menu-xdg
update-menus

---

