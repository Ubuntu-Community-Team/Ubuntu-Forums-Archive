---
title: "Confusing results of upgrade to 10.10"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by Epsilon@pree on 2010-11-20
I upgraded my Acer One netbook using the Network install as I dont have an attached CD. 
 
Apart from it taking about 10hrs to install, everything looked to have gone ok. The machine boots with the following errors, Udevd[80] worker [234] did not accept the message -1 connection refused. 
 
it then goes to to the galaxy screen and then the login screen. I enter my login details and I get a blue background with a mouse, no desktop. I can move the mouse but thats it. 
 
If I press ctrl-alt-del then I get the usual options to power down, suspend, etc. 
 
Any thoughts ?
 
thanks in advance

---

### Post by dino99 on 2010-11-20
try to open a terminal with ctrl+alt+F2 or F7

then:

sudo apt-get dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

if you cant open a terminal, try to boot on recovery mode, then do as above

---

### Post by Epsilon@pree on 2010-11-21
Hi, thanks for the response. I ended up doing a new install from a pen drive whic seems to have worked. Although I still get the initial error above.
 
thanks again

---

