---
title: "Error after installing"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by StevenRitter on 2012-03-15
after installing Ubuntu 11.10 with wubi installer I started it and this is what happens. its like overlapping itself. I can still login in
[IMG]http://i30.photobucket.com/albums/c324/FrankSenka/Photoon2012-03-15at1321.png[/IMG]

When I login this is what happens.....
[IMG]http://i30.photobucket.com/albums/c324/FrankSenka/Photoon2012-03-15at13212.png[/IMG]
Need help! thanks!

---

### Post by bcbc on 2012-03-15
What graphics card do you have?
Have you tried the 2d logon? (click on the settings 'cog' on the login page and change it)

---

### Post by StevenRitter on 2012-03-15
Its a nvidia. Not sure what exactly. I am using a HP DV6000.

---

### Post by StevenRitter on 2012-03-15
ok i found out. its a nvidia gforce 7150m

---

### Post by bcbc on 2012-03-15
So you would look under 'additional-drivers' and install the nvidia driver. (It should prompt you with an app-indicator - top right of screen). If you can't see enough to change it, then boot with the 'nomodeset' option: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

PS if you need to force shutdown use [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot") (to prevent filesystem corruption)

---

