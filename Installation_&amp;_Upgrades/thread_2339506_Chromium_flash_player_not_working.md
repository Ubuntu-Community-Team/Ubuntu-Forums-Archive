---
title: "Chromium flash player not working"
date: 2016-10-09
forum: Installation &amp; Upgrades
---

### Post by Hankbonk on 2016-10-09
I have recently installed lubuntu 16.04 . 

In chromium, the flash player does not work .  How can I install the best flash player for Chromium ?

Underneath two screenshots  from Facebook, the first selecting the app "Riddle stones", the second with the error message :

[ATTACH=CONFIG]271562[/ATTACH][ATTACH=CONFIG]271563[/ATTACH]

---

### Post by howefield on 2016-10-09
Install the adobe-flashplugin package from the Partners repository.

Load up the Software & Updates application and from the Other Software tab check the Canonical Partners option.. then

```
sudo apt update
```
```
sudo apt install adobe-flashplugin
```

---

### Post by Hankbonk on 2016-10-09
Dear howefield

This only reinstalled flash plugin for Firefox, I do need to install it in Chromium

---

### Post by howefield on 2016-10-09
Please keep the font to the default properties, thanks.

The package adobe-flashplugin will install 2 version of flash, the NPAPI version that Firefox will use and also the PPAPI version that Chromium will use.

[https://launchpad.net/ubuntu/+source/adobe-flashplugin/1:20160913.1-0ubuntu0.16.04.1](https://launchpad.net/ubuntu/+source/adobe-flashplugin/1:20160913.1-0ubuntu0.16.04.1)
```
adobe-flashplugin (1:20160913.1-0ubuntu0.16.04.1) xenial; urgency=medium

  * New upstream releases
    - NPAPI: 11.2.202.635
    - PPAPI: 23.0.0.162
```

---

### Post by Hankbonk on 2016-10-09
Sorry for the fonts.

you helped me very quickly, I forgot to restart chromium, I apologise .

---

### Post by howefield on 2016-10-09
> **Hankbonk said:**
> Sorry for the fonts.

I still do not have a working flash player in chromium, it still gives "couldn't load plugin", the second screen on my first post .

If you visit the page below, what version of flash does it say that you have ?

[http://www.adobe.com/uk/software/flash/about/](http://www.adobe.com/uk/software/flash/about/)

---

### Post by Hankbonk on 2016-10-09
Read edited post #5 please .

I will mark this thread as solved .

---

### Post by howefield on 2016-10-09
Cool, glad you sussed it out.

---

