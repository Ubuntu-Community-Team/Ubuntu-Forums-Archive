---
title: "Tried to update Ubuntu Hardy to 10.04 LTS PROBLEMS!!"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by lonewolf454 on 2010-11-28
I tried updating Hardy Heron LTS to 10.04 LTS via install cd (not live cd)

It complained about a couple of errors upon completion.  All of my settings, favorites, and compatible programs are intact after update.

However, I am having multiple issues now, it has crashed at boot a few times, complaining about *ERROR* Forcing to 32M GART size (because of ASIC bug ?)  and  
E: nvidia-kernal-common subprocess installed post-installation script returned error exit status 1

This is on a Gateway MT3707 multiboot XP/Vista/Ubuntu using GRUB as boot manager.  I did not replace conf file /etc/login.defs when I updated.  There are multiple accounts in Ubuntu and XP

I also am having issue with switching user where screen just goes crazy instead of login screen coming up.

Will I have to upgrade or is there a way to fix this update?  It did ask me to update once something about missing a few files, but I only have dialup and the only way to do this would be from the cd.  Please help.

---

### Post by lonewolf454 on 2010-11-30
bumping this back up,

any advice appreciated.

---

### Post by akand074 on 2010-11-30
I don't know if there is a way to fix that upgrade personally. But upgrades often cause people problems. Especially since you went all the way from Hardy all the way to Lucid. I suggest you just do a clean install. Wipe your entire Ubuntu system and reinstall the new version from scratch. Especially if you plan on keeping it until the next LTS release you might as well start clean. Personal opinion anyways.

---

### Post by sikander3786 on 2010-11-30
Please try these commands from the terminal and post their outputs.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

You need access to internet for the first 2 commands. You can say no by pressing "N" if you see the download size is too much for your dial up connection and proceed to the next command.

---

