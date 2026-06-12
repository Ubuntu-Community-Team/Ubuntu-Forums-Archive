---
title: "Gutsy Install on PS3, Bluetooth Works but devices not connecting"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by Rev_Chris on 2007-11-13
I just clean installed Gutsy on my ps3 , it looks and runs pretty decent. Except I cant seem to get the bluetooth to work. 
When i check in bluetooth prefrences I can see the Rocketfish Keyboard/mouse listed , get their mac addresses , ect ect but they just wont control anything.
I enabled HIDD and added the mac addresses for the mouse/keyboard to the config file as default but still no luck.
I also installed the bluetooth package.
Any ideas?

---

### Post by Rev_Chris on 2007-11-13
Also I am using the built in bluetooth adapter to attempt this , 
Its name is "localhost -0"

---

### Post by tcrroadie on 2007-11-13
Hi Rev_Chris

Bluetooth support on the PS3 is still being worked on.  I have read that some users are having some success with the use of the custom 2.6.23 kernel that is available.  If you have not yet installed it, I would suggest giving it a try.  

The new kernel can be found here

[2.6.23-rc7 for PS3]("http://rapidshare.com/files/58033319/linux-kernel-2.6.23-rc7_tools.tar.html") 

Download the .tar package and extract it.  Then install the linux-header and linux-image .deb's.  You do not need to install ps3pf-utils or wifi-radar from this package.  Then restart your PS3.  This kernel will also fix broken wifi issues when updating XMB to version 2.0.

---

