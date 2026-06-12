---
title: "problem closing ubuntu unity"
date: 2013-11-07
forum: Installation &amp; Upgrades
---

### Post by rhoward2000 on 2013-11-07
I will try to get this right so as not to confuse you. 
I just upgraded to  ubuntu 13.10 and now I have a problem. When I click on anything in the main screen ( the screen you click to run an app) my screen will freeze up and I have to manually shut dowm my computer to reboot. This is very annoying and this is one of the reasons I tossed windows out the window.
Can someone help me with this problem? When it freezes up I get  Horizontal lines across the screen, which is why I need to reboot
Thanks
R Howard :mad:

---

### Post by phyzik on 2013-11-07
You should check if you have any old packages still installed that might interfere with unity. In terminal (Shift+Alt+T), type this:
```
sudo apt-get autoremove
```
(it will ask you to input you password)

Also, check if all the packages are up to date:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ajgreeny on 2013-11-07
If you had problems in windows as well as ubuntu perhaps there is a hardware problem causing things to go wrong.  Boot a live DVDand run memtest that will appear at the first boot menu (overnight if possible). 

If it shows any memory errors you will need to seek out the faulty memory stick, if you have more than one, and replace it.

---

