---
title: "Problem upgrading from Kubuntu Fiesty to Gutsy."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by waskoD on 2007-10-19
The Distribution Upgrade has been stuck on "Configuring ucf" for several hours.  I have a fairly fast computer, so I know that's not the problem.  Can I safely close the Distribution Upgrade window and try again?  Or will I have to burn a Kubuntu 7.10 LiveCD and install from that?

---

### Post by bmorency on 2007-10-19
I get stuck once in a while too, do you have it showing you what it is doing at the time? sometimes when you upgrade it will ask you if you want to keep the existing config file or not and not show you that it is waiting for user input. i tried to run:

sudo aptitude dist-upgrade 

from the console and i was able to tell it to overwrite the config file.

---

### Post by waskoD on 2007-10-19
The last line in the terminal is just "Setting up ucf (3.001) ...
                   ".

---

### Post by waskoD on 2007-10-19
Closed out of it, tried to dist-upgrade from the terminal, didn't work.  Now adept won't open.  So I guess I'm a bit out of luck now.  And here I thought I could go the rest of the year without having to reinstall.  Oh well.  Not going to stop me from using Kubuntu, anyway.

---

### Post by bmorency on 2007-10-19
how about trying this in the terminal:

sudo dpkg-reconfigure ucf

---

### Post by waskoD on 2007-10-19
I get
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

---

### Post by bmorency on 2007-10-19
reboot your system and try again. maybe a package manager still has that file locked because the upgrade failed.

---

### Post by waskoD on 2007-10-19
Rebooted, just got a Terminal screen.  Logged in, and typed startx, but that just gave me a checkered screen with the cross cursor as the mouse.  I decided to just install Ubuntu 7.04 from the LiveCD I have (since I loaned out my Kubuntu 7.04 one), and will upgrade that in a day or two.  But thanks for the help.

---

