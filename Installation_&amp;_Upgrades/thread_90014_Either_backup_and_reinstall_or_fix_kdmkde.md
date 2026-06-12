---
title: "Either backup and reinstall or fix kdm/kde"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by TheIdiotThatIsMe on 2005-11-14
This might take me a while. I originally used Kubuntu and recently decided I wanted to try Gnome, but couldn't for some odd error, and then tried to remove everything to do with Gnome since my menu's were filled with Gnome programs. Unfortunately, during the removal, it said it needed to shut down KDM which had a current session to run so I said okay, go ahead, thinking it will continue what it's doing in terminal (this showed up in Adept). But nothing ever happened in the terminal, it just sat there. So I rebooted, and now cannot get back into KDE/KDM. If I type in Startx, it just takes me to a gray screen. I've tried redownloading kubuntu-desktop, but it wont let me for some unfilled dependency on a package it wont let me get. 

Does anyone know of a way I may be able to repair my kde or know of a windows program I can use to read ext3 (preferably a FOSS program?) to copy over my data and reinstall?

---

### Post by yesplease on 2005-11-14
You can backup your data from windows with explore2fs (I use version 1.07), it can read ext3 (and ext2).

Because I am a beginner I would backup and reinstall when I made a mess of the installation. It saves time. On the other hand, you learn more by searching for the solution for a few days.

---

### Post by metoo on 2005-11-15
Still no luck?

If you can access the net (via a router) or still have the packages in /var/cache/apt/archives you can use apt from a console:

If you are not at the console after boot hit
CTRL+ALT+F1 or CTRL+ALT+F2 to get to one of the consoles
login with you user id and password...
(or boot into recovery mode which should bring you to a console)

sudo apt-get -f install to fix dependencies

sudo apt-get install kdm
or
sudo apt-get install --reinstall kdm
sudo apt-get install kubuntu-desktop
or again
sudo apt-get install --reinstall kubuntu-desktop

just to give a start.

dpkg is also good to reconfigure.
man dpkg ...

---

