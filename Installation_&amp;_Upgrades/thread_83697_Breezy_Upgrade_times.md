---
title: "Breezy Upgrade times?"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by PhilB on 2005-10-29
Debating whether to go the upgrade route, and hopefully minimising the need to re- install/reconfigure all the stuff I've put on since getting Hoary, or to go for a fresh install of Breezy and spend ages getting everything set up again.
As a rough guide, how long will an upgrade take on 2Mb broadband-Iv'e heard suggestions of leave it running overnight which is not a realistic option, especially as it will only take an hour or so to download and burn a new disc. 
Many thanks
Phil

---

### Post by MichaelM on 2005-10-29
It took me ~3-4 hours to upgrade on a wireless connection that rarely hit 400 kb/sec. 

If you decide to go the CD route, you could just download the iso, mount it, and use it to upgrade.

---

### Post by Albaraha on 2005-10-29
I downloaded the iso file and mount it, then added the repos to sources.list. Then voila.

---

### Post by reet on 2005-10-29
I originally tried the upgrade route and ran into problems with some packages that I had updated to non-ubuntu packages. In particular, I had upgraded the c compiler to the latest and greatest Debian package. After several hours of trying to sort it out, I decided that a clean install would be a better option.

Luckily for me, I have the /home/ directory on it's own partition, so a re-install went very very smoothly. No lost files, program settings, emails, or anything because all that is on a separate partition. Only took 2 hours to completely install and set up Ubuntu to just the way it was in 5.04, and a lot of that time was spent simply downloading packages to install.

---

### Post by PhilB on 2005-10-31
Thanks for the info. 
In view of the the number of non ubuntu packages, it looks like I will be better off downloading and burning, then trying to upgrade from the disc. If that causes problems, I will at least then have the option of a fresh install.

---

### Post by imagine on 2005-10-31
Assuming that you don't decide for a reinstall:

After making a backup, updating the sources.list and commenting out all 3rd party deb-sources from it, checking for broken/duplicate packages etc, first download all the updates.
```
sudo apt-get update
sudo apt-get -d dist-upgrade
```
This will download 500-600MB updates without any user interaction. If needed, you can cancel the download and resume it later. But with your 2Mb/s line it'll take only 40 minutes anyway.
When finished install the new software.
```
sudo apt-get dist-upgrade
```
Repeat this command as often as needed, ie until apt-get doesn't find anything to upgrade anymore. Then install ubuntu-desktop and ubuntu-base and reboot.
```
sudo apt-get install ubuntu-base ubuntu-desktop
sudo reboot
```

If some strings aren't properly translated, you may want to (re)install the various language-packs for your language with Synaptic or the language-selector application.

---

### Post by DWade on 2005-10-31
I have a stupid question?  Why is it taking so long to upgrade and also to install?  That why I am out here looking every Linux distro I can.  Just found this one, and it's slow too?

---

