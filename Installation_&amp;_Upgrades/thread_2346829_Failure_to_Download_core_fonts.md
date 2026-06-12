---
title: "Failure to Download core fonts"
date: 2016-12-19
forum: Installation &amp; Upgrades
---

### Post by Panawe on 2016-12-19
Since the latest upgrade I have been getting a warning pop-up saying "Failure to Download". The package at issue is "ttf-mscorefonts-installer". Try to fix the problem through Terminal but no go so far. Otherwise everything seems okay.

Solutions anyone?

TIA

---

### Post by lisati on 2016-12-19
Please see this thread: [https://ubuntuforums.org/showthread.php?t=2346763](https://ubuntuforums.org/showthread.php?t=2346763)

---

### Post by howefield on 2016-12-19
Have you got the fonts downloaded, you should have Andale Mono, Arial Black, Arial, Comic Sans MS, Courier New, Georgia, Impact, Times New Roman, Trebuchet, Verdana and Webdings ?

Try..

```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```

If that fails I'd suggest purging the package and installing the 3.6 version of the package.

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

will download the package to your Downloads folder, and
 
```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

will install the package.

---

### Post by Panawe on 2016-12-19
Well, that was quick :)

Thanks.

---

### Post by SurfaceUnits on 2016-12-22
The location of the fonts store has been changed on the sourceforge server

---

