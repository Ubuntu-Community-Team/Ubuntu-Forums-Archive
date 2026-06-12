---
title: "How do i make auto login work in xubuntu?"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by twidget on 2007-02-03
Hi,
im trying to get automatic login to work in Xubuntu edgy using
```
sudo gdmsetup
```
and checking the automatic login box. this doesnt seem to do anything besides add a couple of lines of text to my gdm.conf(?) file. timed automatic login works but makes the login screen look nasty. ive tried this on 2 separate boxes with identical results. is this a bug or am i just missing something in the setup?

---

### Post by aysiu on 2007-02-03
Apart from the fact that you're using *sudo gdmsetup* instead of the proper *gksudo gdmsetup*, you seem to be doing everything correctly.

Could be a bug. Are you using Feisty Fawn? Edgy Eft? Dapper Drake? What version of Xubuntu are you using?

---

### Post by kerry_s on 2007-02-03
menu> system> login window> security tab.

---

### Post by twidget on 2007-02-03
I'm using the alternate install disc for Edgy. is there any difference between using sudo or gksudo besides getting the gui login window?

---

### Post by aysiu on 2007-02-03
> **twidget said:**
> is there any difference between using sudo or gksudo besides getting the gui login window? Yes.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by euchrid on 2007-11-25
> **kerry_s said:**
> menu> system> login window> security tab.

I found that the Login Window will NOT appear on the menu in XFCE or GNOME if you have KDM installed. At least, it wouldn't for me. KDM kind of takes over. Remove it using Synaptic or apt-get unless you need it for a specific theme (unlikely if you are running Xubuntu). You do NOT need to uninstall KDE, just KDM! (Also, removing KDM will not affect KDE programs or being able to get a KDE desktop, although it might affect certain themes that rely on it).

I would suggest setting GDM to the default display manager, then removing KDM, and ideally re-booting, or at least logging out. If you end up with a console and nothing else, you can log in and type "startx -- :1" to get the X session back and put things right. This is also useful if you just want to get rid of the Kubuntu login screen and wish to use GNOME or XFCE.

Once you get the Login Window show up in the main menu, it's probably worth setting the default session (in the first tab) so that you can ensure it's set to what you want for the next autologin.

---

