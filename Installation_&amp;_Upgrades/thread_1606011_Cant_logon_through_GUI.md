---
title: "Cant logon through GUI"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by bluIT on 2010-10-26
Hey currently running Lucid x64. After installing tex-common due to there being errors on all app installations (the apps all seemed to work fine though). I am unable to proceed past the GUI logon, the screen just goes black and returns back to the logon screen. I should also note that the PC was setup to automatically login, so it shouldn,t ask me to logon any way.
 
I had installed many updates earlier that day and also the nvidia graphics driver (before updates), rgba gtk+ module, gnome-color-chooser and upgraded nautilius. All which where working fine at the point before tex-common installation.
 
Searched forums and tried solutions listed. But none seem to have helped.
Kinda stuck for ideas...
 
Still can logon from CL.

---

### Post by gmitrev on 2010-10-26
I have exactly the same problem after updating. I can still access the ttys but cannot login through gui. When I try to login in the console, I cannot execute any command using it's alias, I have to use /usr/bin/sudo or /usr/bin/ls instead of sudo and ls. It says there is something wrong with the PATH variable and I think it is the main problem, but I can't solve it.

---

### Post by bluIT on 2010-10-27
After a bit of ripping stuff out and putting it back in (particularly GDM).When my computer boots it logs me in but all i can see to is a terminal window. No menus, icons, window decoration. etc.

I can individually start nautilus, GTK-window-decorator, firefox but only one at a time.

---

### Post by bluIT on 2010-11-17
Didnt solve it. Complete reinstall. Again

---

