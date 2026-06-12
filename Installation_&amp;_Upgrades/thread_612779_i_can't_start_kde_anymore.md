---
title: "i can't start kde anymore"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by lividishere on 2007-11-14
It was working fine but then I enabled the nvidia driver in the system settings thinking I might install compiz. After I enabled nvidia driver my resolution would not set high enough so I then disabled the driver. Well that just killed my desktop altogether. Now I just get command line login and after I log in I still cant start kde with startx or startkde. I rebooted from the live cd and it looks great but it didn't keep the settings. I would like to just reinstall 7.10 from the alternative cd but it doesn't start automatically and I don't know the command to start it. Yes I am newbie

---

### Post by aysiu on 2007-11-14
At the command-line, try ```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/kdm restart
``` and see if that helps.

---

