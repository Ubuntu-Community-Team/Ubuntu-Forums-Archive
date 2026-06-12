---
title: "how to reinstall ubuntu"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by tomslopez on 2006-07-18
I have ubuntu 5.10 I accidentally uninstalled the xserver, I downloaded ubuntu 6.06 on another computer, by the way I don't have dsl where I am right now, so I tried to upgrade but it didn't work, what can I do to fix it or how do I reinstall everything again. I tried to upgrade using the instructions in the wiki.
can anyone help me please.:(

---

### Post by zxee on 2006-07-19
You have deleted your xorg; is that correct? You should be able to use sudo dpkg -i xorg to re-install. Dpkg should ask you to insert the install media. Check out the man page. Hope that helps you.

---

### Post by reacocard on 2006-07-19
to install xserver from command-line:

```
sudo apt-get install xserver-xorg
```

that will install the xserver.

---

### Post by aysiu on 2006-07-19
Yes, no need to reinstall the whole OS. If you want the default installation back, you can do ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by tomslopez on 2006-07-19
> **aysiu said:**
> Yes, no need to reinstall the whole OS. If you want the default installation back, you can do ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

I did all that, and now when I log in I get the graphical login screen but not like before when you could chose the session, and when I log in I don't see the desktop I just see a dark kind of maroon screen with no options. What can I do?

---

### Post by zxee on 2006-07-20
sudo dpkg-reconfigure xserver-xorg
Make sure you know what video card you are using, other hardware specs will be helpful too since the dpkg script will give you the option to set up keyboard, mouse, video card and monitor.

Sorry I see someone else already suggested running dpkg-reconfigure... 
You do need to know what card and video driver to select when you run that script.

---

