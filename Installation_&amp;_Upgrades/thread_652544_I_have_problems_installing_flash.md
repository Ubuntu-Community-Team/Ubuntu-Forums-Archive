---
title: "I have problems installing flash"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by smithit on 2007-12-28
When I installed Adobe Flash Player 9 from the terminal, it says

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.


What should I do?

---

### Post by empthollow on 2007-12-28
if the md5sum is a mismatch then the file is corrupted and you need to try to download it again.

---

### Post by smithit on 2007-12-28
I did but it says the same thing

---

### Post by empthollow on 2007-12-28
what command are you using to install?

---

### Post by smithit on 2007-12-28
I am using:

sudo apt-get install flashplugin-nonfree

---

### Post by empthollow on 2007-12-28
i had a problem with the flash-nonfree package.  It installed ok for me but flash didn't work.  i uninstalled it and just got the package from the webpage.  here is my how to :)

get the package from [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

```
tar xvf install_flash_player_9_linux.tar.gz
```
```
cd install_flash_player_9_linux
```
```
sudo ./flashplayer-installer
```
when it asks for the path to the program enter
```
/usr/lib/firefox
```

that's it. start or restart firefox and you should be fine

---

### Post by smithit on 2007-12-28
Thanks! Flash contents are working now

---

### Post by empthollow on 2007-12-28
yay!, glad to hear it.  that one of those things i usually end up installing off the web site cuz in the end it's just easier.

---

### Post by BobtheGreatZeta on 2007-12-28
Just wanted to say thanks!  Solved my problem as well.  :)

---

### Post by Babbage on 2008-01-04
Solved my Flash issue too, thanks! :)

---

### Post by dopple on 2008-01-05
Also solved mine. Tar muchly. It's funny that this can't just be installed with synaptic.

---

### Post by AnonChap on 2008-01-05
Yeh, it's nice that there's a workaround, but why doesn't the standard way of installing it work? I also had the same md5sum problem.

---

### Post by empthollow on 2008-01-05
yeah, i can't figure that either, someone should probably submit a bug report if there isn't one already.

---

### Post by Blondie on 2008-01-08
See this [thread ]("http://ubuntuforums.org/showthread.php?t=636397") to find out what this is all about.

Basically Adobe will not allow third parties to distribute flash so flashplugin-nonfree downloads flash from their site when you run it, however Adobe recently changed the version that's on their site at the location it's pointing to, causing a right kerfuffle.

---

