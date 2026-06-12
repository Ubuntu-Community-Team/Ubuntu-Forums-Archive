---
title: "Standalone Internet system"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by billbodewig on 2012-05-29
Perhaps someone out there has already seen it done.

What I want is a plain Ubuntu installation with just browser, mail application, mobile modem connection and perhaps kate.
Many times I just want to connect quickly to the internet to check mail or browse so I don't want to wait for all the other programs to load.
I tried to get rid of most of the basic installed packages but it is not always clear at first sight what they do; and as a result my Ubuntu crashes and I have to re-install and start from the beginning.
Alternatively, if someone has the dependencies packages, a complete list, of what for instance firefox, thunderbird etc require.
Appreciate any feedback

and should I succeed I will post here what I did

---

### Post by cortman on 2012-05-29
How about starting with a [MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD") image and building it up from there? Install the base minimal system, install xorg and SLiM, LightDM or GDM, and the DE of your choice- I picked gnome shell.
Dependencies for firefox, thunderbird, etc. should be resolved automatically when you install them with apt-get.

---

### Post by billbodewig on 2012-05-30
Thanks cortman,
feel a bit of a fool since I never really checked what was available from ubuntu other than the fool distro.
Will try and check how it speeds up access

---

### Post by Bucky Ball on 2012-05-30
Minimal install is definitely what you are after, as advised by cortman. Write a list of the apps you want to install first. Plan it. 

Use Xfce4 or Lxde as the desktop environment and apps for the things you want to do ONLY (no fluff) and it will fly. No comparison. I had a minimal that got to the login screen in 12 seconds from boot. My current one, on an old desktop with 1Gb ram and crappy processor, gets there in about 15 seconds. ;)

DON'T, once you have it speedy and purring, install ubuntu-desktop (or any *buntu-desktop) or you will be back at square one; sluggish.

If you need any more help or have any question about the minimal install just post ...

---

