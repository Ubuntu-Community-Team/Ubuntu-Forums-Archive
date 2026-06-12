---
title: "cannot upgrade jaunty to karmic"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wencin on 2009-10-13
for a few days i havent been able to upgrade to karmic. im using the update manager to upgrade, and it said that i have to run partial upgrade. however, after finished downloading files this message appears:

The upgrade is now aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

and then another message will appear (please take a look at the screenshot)

what should i do to upgrade? and will it really cause unusable state? how to avoid it?

what i notice now is that i cannot right click on my desktop and cannot put any items on it, although it can be accessed from /home/user/desktop. the trash bin also cannot be opened.

---

### Post by Jimmyfj on 2009-10-13
Try and go to System>Administration>Synaptic and launch the program.

Once you've got Synaptic open click on the tab at the left side window saying Custom filters. Click on the tab named Damaged and look for any damaged packages in your install. If there are any damaged packages you'll need to fix them either by deleting the entire package or by upgrading those packages that are damaged.

---

### Post by anewman on 2009-10-13
You need to uninstall open office (this is causing the conflict, look in the terminal). I had exactly the same issue when I upgraded, and when I got rid of OO the rest installed, but not without issues unfortunately and am currently struggling to get a full install to work.

---

### Post by wencin on 2009-10-13
after removing open office the upgrade was successful
thanks a lot

---

