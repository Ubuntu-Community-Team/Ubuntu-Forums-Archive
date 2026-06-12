---
title: "Ubuntu 6.06"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by jsb1022 on 2008-01-24
I installed Ubuntu Server 606 and I am having trouble installing a GUI. I know, why put myself through this extra work and whay did I install server in the first place?  Well - I dont feel like redoing everything. So how di I get the Gui?  I;ve tried apt-get install ubuntu-desktop and dpkg-reconfigure xserver-xorg. Neither works.

Thanks

---

### Post by PmDematagoda on 2008-01-24
What do you get when installing ubuntu-desktop using apt-get? Also post the specifications of your PC.

---

### Post by zvacet on 2008-01-24
```
sudo nano /etc/apt/sources.list
```

Add this line 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

Save and close the file.

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

