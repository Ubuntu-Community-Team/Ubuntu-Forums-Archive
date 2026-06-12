---
title: "Marking packages as DO NOT UPGRADE"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by UrbenLegend on 2007-05-04
I recently compiled ffmpeg for mp3/xvid/aac support and installed the resulting packages. However, the upgrade manager keeps wanting me to upgrade to the default feisty packages that do not have mp3/xvid/aac support. How do I mark them so that they are not upgraded? I've tried locking them in synaptic, but the upgrade manager still pops up. Any suggestions?

---

### Post by benanzo on 2007-05-04
I'm not sure why update-manager is still proposing updates on that package if you've locked it in Synaptic.  I've had to install debs which have (usually older) versions in the repos before and I stopped getting the update notifications when I locked the version in synaptic.

---

### Post by UrbenLegend on 2007-05-06
Yeah locking the packages in synaptic doesn't prevent the update manager from popping up. You can even click update and it will OVERRIDE the locked, compiled packages with the crippled ones. Does anyone know of a way to hold a package in the update manager?

---

### Post by UrbenLegend on 2007-05-07
Okay, I've figured it out. You have to use this old terminal program called dselect.

Type "sudo dselect" into the terminal and then select "Select".

Search for the packages that you want by typing /.

Press = on the packages that you want to hold.

Press Enter and select Configure and then quit.

The update manager stops nagging you now!!!!

Thanks for the help anyway benanzo.

---

