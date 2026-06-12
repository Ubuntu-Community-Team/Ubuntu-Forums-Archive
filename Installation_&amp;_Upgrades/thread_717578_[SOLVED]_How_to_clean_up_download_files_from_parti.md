---
title: "[SOLVED] How to clean up download files from partition /"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by ranser on 2008-03-07
I am running Ubuntu Gutsy and I have downloaded and installed KDE 4.01 (big mistake) and then tryied to uninstall it piece by piece because I didn't find any easy straightforward way to uninstall it all at once. Then I downloaded LG3D looking glass project and tried to install it but a message showed up "disk 100% full", and when restarted the gnome wouldn't take off because of lack of space. I uninstalled from failsafe some apps and freed a bit of space and now gnome starts and runs. I would like to clean the files for both kde and looking glass project installations and maybe remains from other programs/packages (my / is now 98% full, my home is on a separate partition), the problem is I am new to linux and don't know where to look and what to remove and how. Any help wellcome.

---

### Post by wpshooter on 2008-03-07
Probably not what you want to hear, but if it were me I would probably re-install Ubuntu from scratch and give the O/S a good bit more space this time.

---

### Post by uberlube on 2008-03-07
Dido. Clean install would be best at this point as it would be almost impossible to completely remove every trace of KDE 4 from your system.

---

### Post by forestpixie on 2008-03-07
first of all I have no idea how to clear the 2 you're trying to get rid of, but the LG3D should only be the downloaded file if you've not installed it yet so it'll only be the KDE4 files that are installed

sudo apt-get clean 

will remove all the downloaded packages which should get you a bit of breathing space

or alternatively - if you have a seperate /home, would it be too much trouble to reinstall - you can use aptoncd to get all the downloaded debs so that'll help (unless you've used apt-get clean

---

### Post by ranser on 2008-03-07
I have used apt-get clean and it saved me some 400 mb and it should help me hold on until hardy release and then I'll do clean install. Thanx to all.

---

