---
title: "Ubuntu Studio on CD ?"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by ayskura on 2007-09-12
Hi there I'm interested in installing Ubuntu Studio on a PC (as there isn't a version for PPC Macs).
 the only problem I'm having is that the Pc I got has only CDs and the Ubuntu Studio is in DVD... is there a way to split the DVD into two CDs or similar??? 


or maybe is there the 2 CDs downloadable from the Ubuntu Studio Website???

thanks!!!

---

### Post by por100pre1 on 2007-09-12
If you have a web connection and you are using Feisty do this:

```

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

```
```

wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```
```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

This transforms Ubuntu Feisty  into Ubuntu Studio with all its software.

EDIT: If you don't have Feisty installed go ahead and install regular Feisty and then do the procedure shown above.

---

