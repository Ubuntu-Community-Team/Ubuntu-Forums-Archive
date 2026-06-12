---
title: "sources.list"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by nano -i on 2007-04-12
Hi there !
I made a few dumb mistakes while I was editing the sources.list file.
Now it would be nice if someone could upload or post the content of the original file.
(I'm useing dapper Drake 6.06 i386)

cheerio :)

---

### Post by taurus on 2007-04-12
Maybe this is what you need.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by AdotB on 2007-04-12
Its a good idea to make a backup of any important file before editing it. 
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
to resore this just copy it back:
```
sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list
```
I do this with sources.list, fstab, menu.lst, etc...

---

### Post by bashologist on 2007-04-12
Here's a short little script I use to backup important files.
```
backups="$HOME/.backups/"
mkdir -p "$backups"
sudo cp /etc/X11/xorg.conf /boot/grub/menu.lst /etc/fstab /etc/apt/sources.list "$backups"
```

---

