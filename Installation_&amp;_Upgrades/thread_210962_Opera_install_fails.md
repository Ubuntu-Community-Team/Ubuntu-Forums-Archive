---
title: "Opera install fails"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by cotcot on 2006-07-07
When i install opera according to [https://help.ubuntu.com/community/OperaBrowser]("https://help.ubuntu.com/community/OperaBrowser")I  get the error "conflicts with the installed package 'opera' " although i have removed it with apt-get remove and synaptic. It is the same with opera 8.54 and 9.0. Although the error it installs opera but opera cannot connect to the net. I had 8.54 in breezy without any problem. 
Any ideas ?

---

### Post by cotcot on 2006-07-08
Problem solved. Still do not know the reason.
I manually deleted the ".opera" folder in my home directory, uninstalled opera with synaptic and reinstalled opera with dpkg -i opera..... . deb .

---

