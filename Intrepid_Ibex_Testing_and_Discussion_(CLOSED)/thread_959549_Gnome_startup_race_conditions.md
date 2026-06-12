---
title: "Gnome startup race conditions"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by billstei on 2008-10-26
There are two race condition problems in Gnome that I have experienced going back to Hardy and maybe Gutsy, and now continuing in Intrepid:

1) The login background image that I get varies (might not be Gnome per se).  Sometimes I get the one I picked (has a big yellow flower in the bottom right corner), and sometimes I get a default Gnome image (no flower).  This happens both initially when booting up, and also when logging out/in from an already running Gnome.

2) The Notification Area sometimes shows the icons of various startup programs as chosen via Preferences->Sessions->Startup Programs, sometimes not.  Often a small "window" (about 10x30 pixels or so) appears in the top left corner of the screen, which I assume is the lost tray icon.  KDE apps are especially problematic (KALarm for example), although if I manually start them after Gnome is fully loaded/settled, the icon (usually) appears normally.

Anyone else have these issues?

Bill

---

### Post by ciscosurfer on 2008-10-26
Are you upgrading from version to version or doing a clean install each time?

---

### Post by billstei on 2008-10-26
Intrepid was an alternate CD upgrade.  Memory fades on Gutsy and Hardy, but I think Hardy was a clean install.

---

### Post by billstei on 2008-10-26
As a workaround I put this command in for the problematic KAlarm startup launcher (in System->Preferences->Sessions->Startup Programs):

sh -c "sleep 10 && kalarm"

and that was enough to make sure the KAlarm icon ends up in Gnome Notification Area (as opposed to just running apart from it).

Bill

---

### Post by billstei on 2008-10-27
Figured out the login background image issue... in System->Administration->Login Window->Local both the Circles and the Happy Gnome themes were selected, and the Theme pull down was set to Random From Selected.  Makes sense, but I don't think I set it this way.  Maybe it came in via upgrading (?).

Bill

---

