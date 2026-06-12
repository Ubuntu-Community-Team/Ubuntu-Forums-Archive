---
title: "upgrade from 11.04 to 11.10 looks bad"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by yedidel on 2011-11-03
I upgraded to 11.10, now my desktop looks really "old-fashioned", I cannot change resolution to higher (I have the option, but clicking Apply does nothing).

Also, was the option to use Gnome Classic removed in 11.10? can't see it anymore.

screenshot attached to see what I am talking about...

---

### Post by Frogs Hair on 2011-11-03
I don't know about the Win 95 look because I don't upgrade. The cause may be the gnome-settings-daemon . See the links for getting back to Classic .

[http://ubuntuforums.org/showthread.php?t=1859960](http://ubuntuforums.org/showthread.php?t=1859960)

[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)

---

### Post by TBABill on 2011-11-03
Resolution may be a limitation of the driver you are using. If you have an older card it may not be supported other than by the open source driver. I'm in that boat myself. You can log out and log back in, but right after clicking enter when you put in your password, click the little sprocket icon and select 2D. Your system may be more repsonsive that way.
 
The classic you mentioned was from Gnome 2, which is no longer used in 11.10. It's based on Gnome 3. You still have DE options, but not the classic as you are accustomed.

---

### Post by pavi_elex on 2011-11-03
Go to log-in screen, unlock it & 
select ubuntu classic (No effect) as default session.
and restart it.

---

### Post by yedidel on 2011-11-03
> **pavi_elex said:**
> Go to log-in screen, unlock it & 
select ubuntu classic (No effect) as default session.
and restart it.

this option is no more available in 11.10...

---

### Post by yedidel on 2011-11-03
> **Frogs Hair said:**
> I don't know about the Win 95 look because I don't upgrade. The cause may be the gnome-settings-daemon . See the links for getting back to Classic .

[http://ubuntuforums.org/showthread.php?t=1859960](http://ubuntuforums.org/showthread.php?t=1859960)

[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)

thanks, I used the first option, now it's a bit better.
I am with the classic gnome interface but no System menu, and have no idea how to add quick launch to the panel

---

### Post by yedidel on 2011-11-03
> **yedidel said:**
> thanks, I used the first option, now it's a bit better.
I am with the classic gnome interface but no System menu, and have no idea how to add quick launch to the panel

also... opening a folder via places launches gwenview now.
I didn't imagine that a small live-update between 11.04 and 11.10 will cause such a mess...

---

### Post by darkod on 2011-11-03
The gnome3 classic option will be present at the login screen but you have to install the gnome desktop. Sorry, don't know the exact command, but google has plenty of manuals.

You can check for a video driver by opening the Dash, in the search field just enter driver and it will find the Additional Drivers application. Open it and let it search for drivers. If it finds, activate it and reboot.

You could also visit the manufacturer website and look for drivers for your card, download and install.

---

### Post by LinuxFan999 on 2011-11-03
Upgrading Ubuntu within Ubuntu is not a very good idea. The best way to upgrade is to back up your data, burn a CD of Ubuntu 11.10, do a clean install, and copy back all of your data when you are finished.

---

### Post by darkod on 2011-11-03
> **LinuxFan999 said:**
> Upgrading Ubuntu within Ubuntu is not a very good idea. The best way to upgrade is to back up your data, burn a CD of Ubuntu 11.10, do a clean install, and copy back all of your data when you are finished.

If I might add, my personal favorite is to use manual partitioning when installing, create one / partition, separate /home partition and the swap partition.
In every next install, you can do clean install again with the manual option, select the / to be formatted and the /home just to be used as /home (NEVER FORMATTED). It will even keep most (if not all) of your settings.

I have my computers set like that since 9.10 (my first use of ubuntu), and I do clean install when ever I want to. I don't even need to backup and restore my favorites, etc, they are in firefox straight away because the profile is kept in the Home folder which stays the same.

I definitely recommend separate /home partition and then fire away with clean installs when ever you want.

---

### Post by pavi_elex on 2011-11-04
It worked for me,

[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)

---

### Post by pavi_elex on 2011-11-04
[URL="http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/"]
[/URL]

---

### Post by christophevr on 2011-11-04
> **pavi_elex said:**
> It worked for me,

[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)

Hello Indeed this work's. But the system panel is missing . That was my most used panel. The system panel was well removed by Gnome self. Ubuntu can't do anything at it.

Working with the fall back is not the best solution. Since the gnome2 fall-back-pannel is deprecated. This problem will in future revisions come up again, then You will not have this panel at all.

This is personal.
If You need in future all the options and settings in gnome back, You will have to install gnome-shell . That's the new working way of gnome3 . At start it's difficult as it's a new way off work I found myself like I saw gnome for the first time. Once used it becomes much better.

The best way to do is : Open terminal (ctrl+alt+t)

sudo apt-get install gnome-shell gnome-tweak-tool gnome-system-tools gnome-dconf-tools synaptic

Restart ubuntu and select gnome instead of ubuntu or gnome(classic)

It takes time to understand the use and to be familiar with it. But everything is back except the system panel. The advanced settings you will find will give you the opportunity to enable minimize maximize buttons and so on ...

You even can start unity 2d launcher , then You also will have the unity launcher on your desktop.

---

### Post by yedidel on 2011-11-05
> **LinuxFan999 said:**
> Upgrading Ubuntu within Ubuntu is not a very good idea. The best way to upgrade is to back up your data, burn a CD of Ubuntu 11.10, do a clean install, and copy back all of your data when you are finished.

that's what I usually did, but upgrading from 11.04 to 11.10 I expected to pass right...

anyway, if you can't really upgrade Ubuntu, why offer this option? I think it's time that users should be able to upgrade safely

---

