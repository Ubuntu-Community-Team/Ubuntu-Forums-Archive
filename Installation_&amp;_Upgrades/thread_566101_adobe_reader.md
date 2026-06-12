---
title: "adobe reader"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by lrdnitecon on 2007-10-03
im trying to install adobe acrobat reader. im running gutsy. i tried downloading adobe as an rpm file but has nothing to open it with. then i tried to install using wine and downloaded the .exe file and it says it was installing but its not showing up anywhere. does gutsy have a pdf reader? what should i use to open a .rpm file? any help on this would be great. thanks.

---

### Post by forestpixie on 2007-10-03
to use and rpm you need to install alien first, [this]("http://www.psychocats.net/ubuntu/installingsoftware") page might help

or you could install from synaptics, there's a version in there - search for acroread

---

### Post by santiagoward2000 on 2007-10-03
I installed it using the Medibuntu repository, but I'm using Feisty. I looked at their page: [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/) , but they don't seem to have a repository for Gusty yet. Sorry I can't be of much help.

---

### Post by lrdnitecon on 2007-10-03
my acroread is empty in synaptics

---

### Post by forestpixie on 2007-10-03
follow the web link then - if there's no medibuntu for gutsy yet it won't be there. Haven't got gutsy on at the mo, so can't check - thought I'd installed it there as well

---

### Post by disraeli on 2007-10-03
I don't know about Gutsy but don't need to run Acroread using wine, the linux version runs just as fine (I use it under Feisty)

---

### Post by Seisen on 2007-10-03
I use the Medibuntu repository for feisty now with Gutsy and have had no problems. If there is a newer package in Gutsy than their is an the Medibuntu repository it will just pull the one that is the newer version.

---

### Post by Bablefish on 2007-10-03
If you checked the Adobe site a bit more carefully like clicking on the link to other versions you would of discovered that the reader also has a deb download.

---

### Post by n_dimos on 2007-10-05
I wanted to install Adobe Reader 8.0 at my Gutsy but there was only the rpm. Using [Alien]("http://kitenet.net/~joey/code/alien/") to make a .deb from the .rpm i got it installed.

The command i used was:
```
$ sudo alien --scripts AdobeReader_enu-8.1.1-1.i486.rpm
```

the .deb created can be found [here]("http://users.teilam.gr/~n_dimos/adobereader-enu_8.1.1-2_i386.deb") (press Right Click --> Save As...).

---

### Post by Bablefish on 2007-10-05
You can select the deb version from this link

[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

---

