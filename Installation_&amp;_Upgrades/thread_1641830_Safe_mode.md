---
title: "Safe mode ??"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by simpelmees on 2010-12-09
Hi, I installed ubuntu 10.10  on my new sdd and at first everything worked fine. Then i got a list of updates that needed to be installed so I installed those. Since then almost every time i boot in linux, it loads in something that looks like safe mode (light gray), i cant change the looks, but i can surf/ watch movies use apps, ... . The only strange thing i noticed beside this is a red/purple flicker between the screen with the flickering  "-"  and the login screen. Does anyone have the same problem or any recommendations?


System specs:

-1tb hdd with win7
-80gb ssd with ubuntu 10.10 64 bit edition
-4 gb DDR3
-Ati Gigabyte hd5870 
-Asus mobo
-amd x6 1090t

---

### Post by sikander3786 on 2010-12-10
Press Ctrl + Alt + F1, login to the tty1 using your credentials and try to reconfigure your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot!

```
sudo shutdown -r now
```

---

### Post by simpelmees on 2010-12-17
Hey , thanks a lot I did what you said and It runs in the selected visual style again, so it worked. I can't use visual effects now though, but it theres no driver so I'll just try to reinstall graphics driver.

---

### Post by sikander3786 on 2010-12-17
Glad to know it worked for you :-)

You can find the Drivers under System > Administration > Additional Drivers sub-menu (if your graphics card is supported). If they don't seem to appear there, you can download the binaries from manufacturer's website. The first method is preferred though.

You can mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

