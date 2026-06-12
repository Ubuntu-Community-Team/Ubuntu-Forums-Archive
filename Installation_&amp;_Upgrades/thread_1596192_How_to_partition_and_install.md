---
title: "How to partition and install"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by GuitarG20 on 2010-10-14
Hey guys,

(if this is too noob then just have a admin delete the thread)

anyways I have always used Ubuntu with Wubi, and have gone through more than 1 failure (and corruption of the windows boot kernel) because of it. I want my Ubuntu back, and now I have a big enough (500gb) hdd to partition and install ubuntu. does anyone know of a place with a complete guide as to how to do this? I am fine not sharing data between the two; all my important files are in dropbox. but i also do not want to brick my computer...

thanks!
-Greg

---

### Post by krishnandu.sarkar on 2010-10-14
Create free space of say 20GB and then boot from Ubuntu Live CD, it would automatically detect that free space. To make it sure look at the graph of installation that will be presented. If it doesn't detects automatically then select manual partitioning and create:
swap : 1GB
/ : 10GB
/home : remaining 9GB

Well...swap and / is must, /home is your choise, but /home is recommended if you don't want to loose your data or backup them while formatting.

All the figures I've mentioned here are assumption based on total 20GB for Ubuntu, If you want to allocate more space then just make it sure that you allocate no more than 1GB to Swap, allocate most of the space to /home and /

You can also create /boot of 100MB if you want.

The theory is everything is under /, if you don't create this /home, /boot etc this will be automatically created under /, but if you allocate separate space to them then it won't be created under /. And as I said creating /home is highly recommended if you don't wan't to loose or backup your data while formatting next time.

---

### Post by Rubi1200 on 2010-10-14
Hi,
here are some guides that I hope will be useful:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by GuitarG20 on 2010-10-14
allright thanks guys!

I will get on this as soon as I get done with my homework; backing up windows now LOL

EDIT: make that tomorrow. too much hw; i can't risking having to reinstall anything xD

---

