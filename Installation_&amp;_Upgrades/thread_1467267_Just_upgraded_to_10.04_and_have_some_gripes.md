---
title: "Just upgraded to 10.04 and have some gripes"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by timmyhiggy on 2010-04-30
**History:** Installed 9.04 back when I first got my NC10. Used update manager to upgrade to 9.10 when the stable version was released. Upgraded to 10.04 in the same way today.

**Gripes**: 
1. I can't move stuff on the panel anymore, when I right click on, say, the Go Home applet, I dont have any options other than about, the others are all greyed out. I like to have the main menu applet there and use the windows key to show desktop.
2. This also means I can't move stuff in order to be able to click on a clear bit of desktop and change colour, which I wanted to do because...
3. The Human theme seems pretty broke now. The whole notification area has a white background, in spite of the rest of the panel being the translucent black I set it to be pre-update.
4. Some new mail manager app thingy has sprung up in the notification area and I have no idea how to remove it. I use Gmail, so I don't really want that plus the Gmail notifier.
Switching themes changes this and whilst I could get used to the new icons, I'd like to be able to have the top bar as black again.
5. Screen flickers occasionaly. Glad I'm not epileptic!

---

### Post by timmyhiggy on 2010-04-30
I have found a work around in that logging into "desktop" mode and adding netbook-launcher and maximus in the startup programs gives me basically the same system as before, with the only remaining issue being the white background which is now only on the gmail notifier.

---

### Post by dino99 on 2010-04-30
all the apps you dont want are installed by default with the met-package ubuntu-desktop, so uninstall it then with synaptic remove the progs.

for the others stuff:

sudo dpkg-reconfigure gnome-panel
sudo dpkg --configure -a

lot of settings can be tweaked with gconf-editor
maybe be install ubuntu-tweak

---

### Post by timmyhiggy on 2010-04-30
Aah thanks that cleaned it up a lot. However, I just found UNR 2D on the login menu and that appears to be EXACTLY what I had before with the exception of the new power manager icon! Ideal!
Only remaining issue is that I thought this was meant to be a super fast start up, but counting (without equipment, so give or take a few seconds...) from the GRUB menu to the login screen revealed it is taking about 40 secs! I thought it was meant to be sub 10? Would a fresh install sort this?
(I have rebooted a handful of times to check whether or not it is due to it learning stuff each boot...)

---

### Post by timmyhiggy on 2010-05-01
Ok. To get full functionality, I:

- Started in UNR 2D (this one let me edit the panel)
- Stopped the current version of netbook-launcher running at     startup and added the generic one
- added maximus to startup list
- added volume applet at startup
- Removed indicator from panel
- Swapped out the go-home applet for a main menu button as i find it a bit slow to click on that and then wait for everything to minimise every time i want to launch an application.

Still not solved the slow boot, although I added profiling which has helped it a bit. Still not sub 20 secs yet though

---

