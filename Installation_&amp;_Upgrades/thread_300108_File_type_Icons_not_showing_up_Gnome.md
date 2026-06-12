---
title: "File type Icons not showing up Gnome"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by ryan on 2006-11-15
I just upgraded to Edgy from Dapper and everything went pretty smoothly but I  seem to be missed the proper for the different files types. Instead of the Open office icon for a .xls file there is a weird funky outline. Folder Icons are intact.

Any ideas ? tks. Seems like the proper GTK packages are installed.

---

### Post by Dr. Nick on 2006-11-15
out of curiousity have you simply tried switching themes?

---

### Post by ryan on 2006-11-15
Yes I did still the same it seems to have something to do with the nautilus picking up the icons for the specific file types.. the system icons like folders, desktop plus the icons on gnome panel for various apps are there.

---

### Post by Dr. Nick on 2006-11-15
I have one idea you can try out, go into your home folder and set it to show hidden files, then rename .gnome and .gconf I believe to .gnomebak and .gconfbak or similar.
 
That will force all the gnome settings to get set back to defaults on the next login which will clear any customization you have done, If that fixes it then you may just have to setup the various custimizations again, if it doesnt fix it then you can just restore the backups
 
Another thing you could try would be creating a new user and see if it works right.
 
Both those are just guesses since I have never had that specific issue before, but it looks like their is some config file that got messed up during the upgrade.
 
Another thing to check to be safe is that ubuntu-desktop package is installed, if it is then their shouldnt be any packages missing.

---

### Post by ryan on 2006-11-15
Ok tks I will check these suggestiosn out it also messes up browsing the windows network that I am on.

---

### Post by ryan on 2006-11-16
The new user deal didn't work, nor reinstalling ubuntu desktop, the renaming of the various folders may have worked but I must have done something wrong and the system wouldn't start the gnome desktop. I copied my /home/ryan folder from my laptop which also has edgy installed. That didn't really work either this is all in terminal. Finally I deleted a some entire folders (the gnome ones) and did apt-get update & apt-get install the components that I deleted and then everything worked fine and I could at least get into my system. The icon issue is still there and I think it has more to do with the mime type definitions which is what I will looking into next. Tks for your help.

---

