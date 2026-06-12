---
title: "How Can I INstall ADobe Photoshop"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by Richt0wnfin3st on 2008-03-19
How Can I Install Adobe Photoshop CS3

---

### Post by hvacr on 2008-03-19
> **Richt0wnfin3st said:**
> How Can I Install Adobe Photoshop CS3


You would have to use wine, but I do not think cs3 works to good with it. I believe cs2 works well with wine though.

---

### Post by Richt0wnfin3st on 2008-03-19
so you ever tried it?

---

### Post by aysiu on 2008-03-19
> **Richt0wnfin3st said:**
> How Can I Install Adobe Photoshop CS3
You can't.

For more details, look at the Wine page for Photoshop CS3
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584)

CS2 might work, however. You use Photoshop-specific features that aren't available in GIMP?

---

### Post by Nathan_M on 2008-03-19
Yeah, like hvacr said, if you have a previous version, I would recommend going with that. Installing CS3 is difficult, and doesn't always work, because it was made for Windows. CS2 is easier.

```
$ sudo apt-get install wine
$ wget http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe
$ chmod +x times32.exe
$ wine times32.exe
```

Install Photoshop as normal from there. I've copied (and hopefully clarified) these steps from [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631). If you have any more problems, ask back here and I'll do my best to help.

Edit: I also recommend Gimp. It's free, works perfectly with Ubuntu, and should already be installed. There's not much PS can do that Gimp cant

---

