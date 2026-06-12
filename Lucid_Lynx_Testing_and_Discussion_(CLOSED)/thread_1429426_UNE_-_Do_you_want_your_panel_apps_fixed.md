---
title: "UNE - Do you want your panel apps fixed?"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by victor9098 on 2010-03-14
After installing UNE I found that I could not change any of the top panel apps, could not change their position or add new ones as the GUI options are all greyed out (I do not know of another way to add). I have done some digging and found that this is the intent of the developers, from [DesktopTeam/Specs/Lucid/DesktopUNESession]("https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/DesktopUNESession")

> Stay like this, calling it the "UNE experience" where you can't change any applets. This is what I first chose, (as mostly gnome shell take that path too). But we need then to take some shields against community feedbacks (no casual user where we don't expect to change this)

I kept digging and found a guide that I thought would turn the options back on here [UbuntuNetbookEditionConvertGnomeSession]("https://help.ubuntu.com/community/UbuntuNetbookEdition/ConvertGnomeSession") which suggest doing the following:

> 3D Ubuntu Netbook Edition Session
In a terminal run:

sudo ln -s /etc/xdg/xdg-une/autostart/maximus-autostart.desktop /etc/xdg/autostart/
sudo ln -s /etc/xdg/xdg-une/autostart/netbook-launcher.desktop /etc/xdg/autostart/
to start the UNE Launcher and Maximus (window maximizer) at login. Then run:

sudo ln -s /usr/share/gconf/une/default/20_une-gconf-default /usr/share/gconf/defaults/
sudo ln -s /usr/share/gconf/une/mandatory/20_une-gconf-mandatory /usr/share/gconf/defaults/
sudo update-gconf-defaults
to set the gconf default settings.

I did all that but when logged in I see no difference and can not make alterations to the panel. So it looks like they intend to lock end users panels for the next 3 years at least. Though I do not completely support their logic, if someone has gone out of their way to install UNE onto a machine, then there is little trouble to install the normal desktop edition. While the times I have logged into the GNOME session I am just met with a blank desktop with nothing more then the top panel with just the clock!

Is anyone aware of other fixes or workarounds for this?

---

### Post by victor9098 on 2010-03-14
Ok, now I get it. After doing the above suggestions you choose to login to the GNOME desktop and it looks like the standard UNE now, but you can edit the applets.

Seems to be a very awkward way of doing this, all the previous editions of UNR worked fine as standard and I have used each one.

---

### Post by skrimpy on 2010-04-17
Thank you Victor, this was driving me crazy and your thread helped a lot :)  I've got the UNR "look" and can work on my panel bar again now.  Now off to work on fixing my brightness buttons and figure out why I have no visual effects!  Thanks!

---

### Post by victor9098 on 2010-04-17
> **skrimpy said:**
> Thank you Victor, this was driving me crazy and your thread helped a lot :)  I've got the UNR "look" and can work on my panel bar again now.  Now off to work on fixing my brightness buttons and figure out why I have no visual effects!  Thanks!

Glad I helped, thanks! Yeah, it is alot of effort just to tweak your panel settings, once everybody updates at the end of April then the fun will start :popcorn:

---

### Post by magneze on 2010-04-18
On mine the "Go Home" applet has been placed on the right, but I can't move it to the left. Will try these suggestions.

---

