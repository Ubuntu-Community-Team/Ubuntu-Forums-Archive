---
title: "New install - No GUI? - is it complete?"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by Corbiere on 2006-10-25
Hi,

This is my first time with Ubuntu linux..i'm used to SuSe and some experiance.

I downloaded v6.06 desltop and installed it dual boot with Win XP. I can boot both no problem but Ubuntu just goes to user login?

I looked for the path to start XDM or KDM etc but can't find either.

Is there a gui with the install or do I have to download it elswhere? Or has my install not been complete..I noticed that when it asked to renove the CD and reboot the progress bar was some way off the end!

any help or pointers would be good.

Corbiere

---

### Post by darrenm on 2006-10-25
Are you sure you downloaded the desktop edition and not the server edition?

---

### Post by Bachstelze on 2006-10-25
Hi and welcome to Ubuntu :)

There can be many-many-many reasons why the GUI fails to start. please paste the contents of /val/log/Xorg.0.log

---

### Post by Corbiere on 2006-10-25
oops!.. xorg,log missing and I noticed that screen says ubuntu 2.6.15-26-server so i guess i've installed server version by mistake?

can I convert or is it easy to get the GUI installed? or would it be easier to get desktop version and overwrite?

Corbiere

---

### Post by taurus on 2006-10-25
At the prompt, type

```

sudo aptitude update
sudo aptitude install ubuntu-desktop <-- for Gnome
sudo aptitude install kubuntu-desktop <-- for KDE
sudo aptitude install xubuntu-desktop <-- for XFce4
sudo /etc/init.d/gdm start

```
Just pick one from the list above for Gnome, KDE, or XFce4...

---

