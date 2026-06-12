---
title: "utorrent in wine error"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by okmijn22 on 2010-01-14
Hey I try to install utorrent with wine however when I install it, I get the error message
"It seems like utorrent is already running but not responding. Please close all uTorrent processes and try again"
Thanks for your help.

---

### Post by Dayofswords on 2010-01-14
why go through the trouble, there are bittorrent clients for linux,

[Deluge]("apt:deluge") is good

---

### Post by heymish on 2010-01-15
I found this helped
[HTML]
http://appdb.winehq.org/objectManager.php?sClass=version&iId=11113&iTestingId=45353[/HTML]

If/When you get this error:

It seems like uTorrent is already running, but not responding. Please close all uTorrent processes and try again.

you could simply kill all the utorrent processes with:

```
killall -9 uTorrent.exe
```

Then just open utorrent, not the installer.

You can also open µtorrent with '/NOINSTALL' parameter but then you can't change any settings (if I understood right). E.g.:

```
C:\Program Files\uTorrent\uTorrent.exe" /NOINSTALL
```


Hope it helps

---

### Post by Rob@ThePCWiz.info on 2010-01-15
DUDE
```
sudo apt-get install transmission
```
or
```
sudo apt-get install ktorrent
```

And hell even the Opera Web browser downloads torrents just like any other web browser downloads a direct download.
```
sudo apt-get install opera
```

---

