---
title: "Upgrade Ubuntu 7.04 to Ubuntu Ultimate 1.4"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by TekNullOG on 2007-08-14
Hello,
I use Ubuntu 7.04 and have had the chance to play around with Ubuntu Ultimate 1.4 using VMware Workstation. I love it and am thinking of making the switch.

The [Ultimate *CD* Edition]("http://ubuntusoftware.info/Ubuntu_Ultimate_CD/") comes with an upgrade file on the Desktop that helps download all additional items (games, drivers, etc...). Can we use this upgrade file with a regular version of Feisty to convert to Ultimate 1.4?

I would prefer avoiding a complete re-installation of my OS.

If I cannot perform an upgrade using only this file, what would I be missing to succeed at doing so?

Thanks

---

### Post by wolfen69 on 2007-08-14
ubuntu ult. is just regular ubuntu with lots of packages preinstalled. and a different theme. see what packages it has that you want, and download them. go to [http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=dd7716424cdfb622eedfb51849eb96c3](http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=dd7716424cdfb622eedfb51849eb96c3) to get the theme.

---

### Post by TheeMahn2003 on 2007-08-14
> **eightinches said:**
> Hello,
I use Ubuntu 7.04 and have had the chance to play around with Ubuntu Ultimate 1.4 using VMware Workstation. I love it and am thinking of making the switch.

The [Ultimate *CD* Edition]("http://ubuntusoftware.info/Ubuntu_Ultimate_CD/") comes with an upgrade file on the Desktop that helps download all additional items (games, drivers, etc...). Can we use this upgrade file with a regular version of Feisty to convert to Ultimate 1.4?

I would prefer avoiding a complete re-installation of my OS.

If I cannot perform an upgrade using only this file, what would I be missing to succeed at doing so?

Thanks

I read you email ;)  Yes as said you could do that however you would not have the upgrade Icon on your desktop to make this happen open a terminal:
```
sudo mkdir /usr/share/ultimate
cd /usr/share/ultimate/
wget http://repoubuntusoftware.info/upgrades/tunez/blackcry.mod
wget http://repoubuntusoftware.info/upgrades/tunez/halloween_theme.s3m
wget http://repoubuntusoftware.info/upgrades/tunez/NIN_HEAD.S3M
wget http://repoubuntusoftware.info/upgrades/tunez/axelfmix.mod
wget http://repoubuntusoftware.info/upgrades/tunez/playlist.m3u
wget http://repoubuntusoftware.info/upgrades/gamers.sh
wget http://repoubuntusoftware.info/upgrades/bootscript.sh
wget http://ubuntusoftware.info/upgrades/ubuntu_ico.png
sudo chmod +x gamers.sh
echo "[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Upgrade
Type=Application
Exec=gksudo sh /usr/share/ultimate/gamers.sh
Icon=/usr/share/ultimate/ubuntu_ico.png
Terminal=True
Categories=GNOME;GTK;Application;System;" > ~/Desktop/Upgrade.desktop

# chmod shortcut
chmod a+x ~/Desktop/Upgrade.desktop

```

This was not designed to be done this way, let me know how it goes.

Best regards,

TheeMahn

---

### Post by Seisen on 2007-08-14
You can just add the Ubuntu Ultimate Repository following the directions here.

[http://repoubuntusoftware.info/#1.4]("http://repoubuntusoftware.info/#1.4")

---

