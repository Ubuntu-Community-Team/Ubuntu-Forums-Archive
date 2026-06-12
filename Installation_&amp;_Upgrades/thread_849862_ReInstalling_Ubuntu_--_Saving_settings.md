---
title: "ReInstalling Ubuntu -- Saving settings"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by whos2know on 2008-07-04
Hi, I need to reinstall Ubuntu for several reasons.  I need to have all my settings and apps or packages at the least to be copied or not copied but to be able to know what was on there previously.  I remember someone awhile ago giving me a command on bash to do this.  A small file was made that I had copy and had all the info.  Then once I had reinstall Ubuntu I would put a similar command in and it install all the packages for me.  

Thanks and Happy Fourth of July!!

--Bobby

---

### Post by tamoneya on 2008-07-04
just keep your home directory.  Backup with:```
cp -R ~/* /some/backup/drive
```

Restore with:```
cp -R /some/backup/drive/* ~
```

---

### Post by oernie on 2008-07-05
Hi!

I have the same problem as tamoneya: re-installing Ubuntu while keeping all settings. Since I want to keep *all* settings (not only the personal settings, which for instance do NOT include the list of all (manually) installed packages), just backing up and restoring the /home partition does not entirely solve my problem.

Background: My laptop computer (Dell Latitude D600) got a new motherboard, because the old one was broken. The new one is almost the same as the old one. However, the new motherboard has newer versions of some chipsets. After changing the motherboard, the network adapters are not working properly any more and my computer freezes every few hours. I guess that the new chipsets require other settings and/or drivers. Unfortunately, running "sudo dpkg-reconfigure -a" did not solve the problem. Hence, it seems that I have to reinstall Ubuntu.

Thanks in advance for any hints,
Oernie

---

### Post by steveneddy on 2008-07-05
Just copy all of the application specific data then.

I always copy my regular stuff from my /home folder, and I pick and choose the folders starting with a dot.

like

**.gnome**

or 

**.fonts**

---

### Post by oernie on 2008-07-05
> **steveneddy said:**
> Just copy all of the application specific data then.

I always copy my regular stuff from my /home folder, and I pick and choose the folders starting with a dot.
[...]

I do not need to (separately) backup the hidden (dot) files and folders in my home directory, because they are on my home partition and, hence, are not effected by a reinstall. However, I want to keep also the system settings (e.g. the list of all (manually) installed packages). How can I do this?

---

### Post by tamoneya on 2008-07-05
use remastersys to make your self a custom installer disc that installs your programs for you.

---

### Post by oernie on 2008-07-06
> **tamoneya said:**
> remastersys

This seems to do exactly what I was searching for.
Thanks a lot!

---

### Post by whos2know on 2008-07-06
hi!

Thanks for all the help. I did indeed find what I needed.  What I ended up doing was copying my home folder and after that used this command

```
sudo dpkg --get-selections >~/Desktop/installed-pkgs
```

Then after installing Ubuntu used

```
sudo dpkg --clear-selections
dpkg --set-selections <~/Desktop/installed-pkgs
sudo aptitude install dselect-upgrade
```

Again thanks for all the help and thank you to drs305 from a different thread!!!

Bobby

---

