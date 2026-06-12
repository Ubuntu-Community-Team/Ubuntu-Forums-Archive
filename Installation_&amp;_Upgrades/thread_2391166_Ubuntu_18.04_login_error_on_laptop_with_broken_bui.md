---
title: "Ubuntu 18.04 login error on laptop with broken built-in display!"
date: 2018-05-06
forum: Installation &amp; Upgrades
---

### Post by jmlm-1970 on 2018-05-06
Ubuntu 18.04 fail to show login screen on laptop with broken built-in display!

If laptop is working with VGA/DVI/HDMI screen, and have the built-in display broken, the login is not working.

A working solution, is (but not the right one, yet):

Boot and select Advanced and use Recovery Mode, when the menu appears, choose resume (click, scroll down, on screen, if login does not appear) and then login with your user;

After sucessfull login, go to settings (best way, just right click desktop and choose to "Change Background");

In the settings go to, Devices, Displays, and choose "Single Display" and choose second display and press Apply and then Keep Changes;

In the settings go to, Details, Users, and press Unlock, and "Automatic Login" ON.

In next reboot, Ubuntu 18.04 desktop will appear (but not the login screen).

Anyone with the right solution, to make login screen appear in secondary screen, instead of built-in display? :)

---

### Post by #&amp;thj^% on 2018-05-06
Well we or someone might need this information also:
```
cat /etc/systemd/system/display-manager.service | grep '/usr/sbin'
```
We need to see if you are using GDM or LightDM

---

### Post by jmlm-1970 on 2018-05-06
No return.

If changed sbin return:

ExecStart=/usr/sbin/gdm3

---

### Post by #&amp;thj^% on 2018-05-07
Thanks ;) some of the small differences between Arch and Ubuntu >> "If changed sbin "
Fixed my code in Post#2 also

The last time I used Gnome was in 17.10 so this should still work for 18.04 also.
Important NOTE:If your ".config monitors.xml" file is set up the way you want your monitors to be set after you log in, try this and reboot. **Note:** that by default there is no existing monitors.xml file under /var/lib/gdm3/.config (at least it wasn't there for my setup.)
```

sudo cp ~/.config/monitors.xml /var/lib/gdm3/.config
```
Also I believe I had to "sudo chown /var/lib/gdm3/.config" back to root owned.

---

