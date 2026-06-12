---
title: "Ubuntu 9.10/Kubuntu question"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scratman on 2009-08-25
Hi guys.  I upgraded to the 9.10 Alpha a few days ago, and have had a few niggles, but nothing major, apart from one thing, I want to try Kubuntu, rather than Ubuntu.  So I went to Synaptic Package Manager, and selected kubuntu-desktop, allowing it to install all of the dependencies it required.  I let it all install, and performed the required restart, but it does not seem to have installed properly. I have still got the standard Gnome window manager, and every KDE app that installed as part of the upgrade fails on launch, with the exception of Amarok.  I get the Kubuntu splash screen on boot and shutdown, but everything else seems to be Gnome.  I assume that I'm doing something wrong.  Does anybody have any ideas?

---

### Post by taavikko on 2009-08-25
At this point would be really more easier to install Kubuntu to other partition than side by side.
And at boot, decide which system to start.

ps. please use more descriptive thread titles, as you now posted two by the same title, creates confusion.

---

### Post by sundar_ima on 2009-08-25
If you really want the taste of Kde4.3 then i would suggest you to install Kubuntu in a different drive instead of installing in a single partition (along with Gnome). I tried this long back but did not get the real kde look. Any way you can try this command **sudo cp .gtkrc-2.0-kde4 /root/.gtkrc-2.0**. This command is just to change the look of gnome applications as kde applications. 

If you start using kubuntu with kde4.3 then you will seriously think of not to go back to ubuntu.

---

### Post by dabl on 2009-08-25
Sound like something snarfed - prolly due to the developmental status.

If you decide to reinstall, just get a Kubuntu daily build ISO image here:

[http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

But wait until this 2.6.31-7 kernel snafu is fixed.

---

### Post by snowpine on 2009-08-25
All you need to do is log out, then from the login screen, choose Sessions->KDE (instead of Gnome).

---

