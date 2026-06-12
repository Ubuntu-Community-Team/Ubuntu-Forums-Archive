---
title: "Hardy 8.04 server - xubuntu-desktop install failed?"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by tra4d on 2008-05-15
Hi

I installed 8.04 server ed. w/o any issues.  I then tried to install xubuntu desktop using the following as per the help/doc'n.:

```
sudo apt-get install xubuntu-desktop
```

However, when I rebooted, the login screen was fine, but the desktop is just a picture of the heron and a terminal window.  No icons, menus, etc.

Any ideas what went wrong?

---

### Post by tra4d on 2008-05-15
Anybody?  I just did an install of kubuntu desktop and got the same results.  Login screen is great, then just the hardy heron wallpaper and a terminal window.

???

---

### Post by tra4d on 2008-05-15
Nobody has ANY suggestions?  Places to look, things to check for?

---

### Post by 4partee on 2008-05-15
Yep, that is exactly what happened to me as well!

---

### Post by RWells on 2008-05-15
Well I dont know anything about it but I did manange to hack ubuntu desktop into 8.04 server, so I will throw some stuff out for you since no one else is.

Can you use the controls on the monitor to resize the desktop?

Can you tell us what your xorg.conf file has in it?

---

### Post by tra4d on 2008-05-16
The monitor was the right size, since the mouse never disappeared off the screen.

This was the xubuntu desktop only, let me clarify.  I had installed the xubuntu desktop, and gotten this issue.  When I installed the kubuntu desktop, it asked some question about being the only blah blah blah and so I ASSumed that it would just switch to kubuntu when I logged in.

However, this was not the case.  On the login screen, when I picked the kubuntu verion, it worked fine.

But I wanted the xubuntu (xfce) desktop.  So I re-installed, and was able to select the xubuntu desktop as part of the initial install (as apposed to using apt-get) by going 'Back' when given the software selection screen - there are only a few options, but when I selected 'Back' and then went forward, I got this huge list of other things to install, including all the x11 desktops/GUIs.

Hope that helps somebody.

---

### Post by garethsimpsonuk on 2008-06-19
It's defo not just me then. Is this a bug? I'm usually good at narrowind down my searches but I'm finding this hard to research

---

### Post by avtolle on 2008-06-19
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) Take a look at this. Perhaps item number 3 of the links on the right side should be considered?

---

### Post by garethsimpsonuk on 2008-06-19
> **avtolle said:**
> [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) Take a look at this. Perhaps item number 3 of the links on the right side should be considered?

Thanx 4the response butI used xubuntu-desktop which is a meta package which should install everything you need. that is referring to starting x after installing only a few packages.

Unless what your saying is that startx isn't staring all the necessary packages but I thought it did. I've done this with gnome and it worked perfectly. Any other suggestions?

By the way I've found a few posts on the forum about this, people don't always post the solution, maybe there isn't 1.

Thanks

---

