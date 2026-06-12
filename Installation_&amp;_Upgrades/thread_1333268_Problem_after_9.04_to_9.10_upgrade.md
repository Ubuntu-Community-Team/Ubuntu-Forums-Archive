---
title: "Problem after 9.04 to 9.10 upgrade"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by mode101 on 2009-11-21
I was running linux on 9.04 and it was running prefectly. I received a notice that an upgrade was available, so I said OK to install it....
 
Problems I have after the upgrade:
 
1) My desktop icons are gone.
 
2) I cannot right click on just the desktop, right click works on the top and bottom bars of the screen, but not right on the desktop
 
3) I have a "Places" drop down on the top toolbar, when I click on places like home folder, desktop, documents, nothing comes up.
 
I have seen other posts with people having the exact same problems after the upgrade, but have not found a 'fix' that seems to work.
 
This box is my oldest computer, but seemed to run 9.04 great. I have a nvidia card, 1gb ram.
 
I am new to linux, sorry if this has been answered before, I really did try to find a fix ;)
 
thanks!!

---

### Post by MiCK.ca on 2009-11-21
Is your information backed up? I had the same exact problem with My wife's PC. 

I did understand going into the upgrade that 9.10 is also upgrading Gnome/Nautilus. this could account for the desktop/icons/toolbar behaviour. i ended up backing up all data and (actually created a separate home partition for my wife) and reloaded. 

Having a separate /home partition will help in the future when an upgrade goes foul and no info will be lost. BUT WAIT! i haven't answered your question yet... anyways, this has happened to more than yourself. In most of these cases people just simply backed up and reloaded FRESH. 

I say backup/ reload/ and enjoy a fresh installation. i ended up doing the same with mine. Trust me having a separate /home partition REALLY saves you headaches.  Fresh is always better. Sorry if this isn't the answer you were hoping for.

---

### Post by intrader on 2009-11-21
I have posted by experience with updating from 9.04 to 9.10. The resulting UI is just about unusable.
I also experience the icons disappearance. And I discovered that System->Preferences->Startup Applications had a large number of applications checked. I have removed 'Blue Tooth, and Evaluation Alarm' and unchecked most of the rest except Network Manager, PolicyKit Authentication, Print Queue Applet, Update Notifier, and Volume Control.The GNOME Settings Daemon and GNOME Settings Daemon Helper seemed to have helped as now the icons are drawn properly and the UI is behaving better.
Without these two GNOME unchecks, the icons did not show up correctly and the UI was just about unusable as the UI was sticky and unresponsive:
1. Click on icon does not cancel and mouse drags the icon image around.
2. Highlighint while typeing is 'sticky'
3. Scrollbar is 'sticky' and scrolls the page while mouse is move in the page area.
4. Click on close takes many tries.
etc.

Try resetting the GNOME entries I describe
It seems better.

Thanks

---

