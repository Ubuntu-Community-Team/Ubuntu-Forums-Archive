---
title: "No xsession after upgrade to 16.04"
date: 2016-10-09
forum: Installation &amp; Upgrades
---

### Post by AbdoulBirane on 2016-10-09
Hello,

I tried to find the info on the forum to no vail, as I am sure I am not the only one it happened. Please show me the link if it IS there.

I upgraded from 14.x (04?) to 16.04 and the boot works well but I have a text prompt to login instead of the graphical list where I can select a user to login.

I can manually login and type commands but I have no idea how to get a session X. 
manual startx fails.

Hope it makes sense and the problem is easy to fix.

Waiting for your questions to know what to report here for more details.

Regards

---

### Post by gdesilva on 2016-10-09
I suspect you have not loaded the correct video driver to start with. Generally, the installation should have loaded the open source driver for your card but if available it would be useful to try out installing the proprietary driver to see whether the problem goes away or not. Firstly, you would need to identify the card in use (check with lspci command which will list all pci devices). Also check out the /var/log/Xorg.0.log to for the specific errors. You can do a quick check by using cat /var/log/Xorg.0.log | grep EE to filter out the error messages or cat /var/log/Xorg.0.log | grep WW to filter warning messages during xserver process initialization.

---

