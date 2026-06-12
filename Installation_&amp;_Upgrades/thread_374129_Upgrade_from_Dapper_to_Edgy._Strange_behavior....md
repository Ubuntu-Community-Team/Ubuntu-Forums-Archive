---
title: "Upgrade from Dapper to Edgy. Strange behavior..."
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by CyberAngel on 2007-03-02
I `ve taken to my hands a Toshiba laptop that had Kubuntu Dapper installed and I did a dist-upgrade to edgy...

Everything went ok except the following strange behavior......

Now after the reboot kdm cannot start!
It shows a blinking underscore "_" in the upper left of the screen and it stays there in a black screen...

If I go to a terminal (alt+ctrl+F1) and login and then check the file /var/log/Xorg.0.log I can see in the last 2 lines the following:

```
Fatal server error:
no screens found
```

So I assume that it cannot load the i810 driver for the laptop`s graphics card.

Now if type startx on the terminal, the X session for the users starts normally!!!
How is that possible?

---

### Post by zvacet on 2007-03-02
```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by lptr on 2007-03-02
Here the same with a Thinkpad Z60m with ATI mobile 600.

Followed this [https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29](https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29)

second method. But: Major difference multiple times aptitude dist-upgrade instead of only three times. Some defaults has been overwritten during upgrade. I repeated dist-upgrade until apt-get update/-f install told me from two held back packages of minor priority. Then I rebooted machine.

X-Server did not start. But system started. So I switched into console (Alt-1) logged in as normal user first sudoed dpkg-reconfigure xserver-xorg, and started X manually (startx). Guess what - Gnome came up. But now I want to have KDE back.

Tried reinstall of kdesktop and kdm. I seems that it is a kdm issue.

Any ideas?

rob*

---

### Post by CyberAngel on 2007-03-05
I did the "sudo dpkg-reconfigure xserver-xorg" but still the same.....

I Can view the X using startx but by default KDM doesn`t come up....
Only the black screen with the blinking cursor :(

---

