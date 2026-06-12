---
title: "Trying to Install Netbook Remix 10.10 but won't"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by heyitztimmeh on 2010-12-09
So I just recently downloaded Ubuntu Netbook edition 10.10 to dual boot with my Windows 7. I successfully installed it and have both running, but it seems that the desktop version of Ubuntu is installed instead. Any help? Thanks :D

---

### Post by sikander3786 on 2010-12-09
Welcome to the forums :-)

The new netbook is 3d and requires to install the graphics drivers thats why I guess it is starting in standard desktop mode.

Go to System > Administration > Additional Drivers and activate the current graphics drivers.

Reboot, from Login Screen, click your user name, Sessions menu will appear at the bottom of screen, select ubuntu-netbook and login.

If drivers are not available, post your graphics card make and model.

Applications > Accessories > Terminal
```
lspci | grep VGA
```

If you've selected auto-login, after reboot, you'll need to log out and then do the steps from Login Screen.

Good Luck!

---

### Post by heyitztimmeh on 2010-12-09
Thank you so much! Your advice worked perfectly. Will it default boot up to the desktop edition or is there a way to make it boot in to the netbook edition?

---

### Post by sikander3786 on 2010-12-09
> **heyitztimmeh said:**
> Thank you so much! Your advice worked perfectly. Will it default boot up to the desktop edition or is there a way to make it boot in to the netbook edition?
You are Welcome :-)

Once you boot the ubuntu-netbook session, it would automatically be made default session. Otherwise you can choose it under System > Administration > Login Screen.

You can mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by heyitztimmeh on 2010-12-09
One more quick question. How exactly do I get to System > Administration > Login Screen in the netbook edition?

---

### Post by sikander3786 on 2010-12-09
Click the Ubuntu Logo in top left corner or the Applications Icon in launchbar ( seems like a pair of scissors) and search for Login Screen.

---

### Post by heyitztimmeh on 2010-12-09
Thank you again sikander3786

---

