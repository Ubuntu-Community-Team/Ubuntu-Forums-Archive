---
title: "Possible to reinstall 12.10 from command line?"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by Gh0zt36 on 2012-12-01
Flash stopped working on certain sites. I tried everything. I installed mint 14 on another drive and it works fine and thats based on 12.10 so I want to re install 12.10 from terminal but I cant find any instructions as I wont be upgrading so the sudo apt-get install distro upgrade . 

Anyone know how to do this?

---

### Post by Frogs Hair on 2012-12-01
I don't think re-installing the desktop will help with flash but if want to, attempt this first. ```
sudo apt-get install --reinstall ubuntu-desktop
```

(Option 2)This is very slow !!!! ```
sudo dpkg-reconfigure -phigh -a
```

> since this command would take a lot of time to process (~1 hour) depending on your hardware in case you have a minor dependency problem you can fix it via.```
sudo apt-get install -f
```

---

