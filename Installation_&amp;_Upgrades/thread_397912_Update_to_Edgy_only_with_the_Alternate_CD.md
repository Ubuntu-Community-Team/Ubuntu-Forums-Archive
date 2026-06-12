---
title: "Update to Edgy only with the Alternate CD"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by FireLink on 2007-03-31
It is possible to update to Edgy from Dapper with the Edgy Eft Alternate CD without going on Internet?

I mean upgrade only what's on the CD.
I'm stuck with dial-up and I do not want to wait 1 day and hours...

Thanks!

---

### Post by zvacet on 2007-03-31
[https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades")

---

### Post by FireLink on 2007-03-31
Already tried... It tries to download all updates even if I said no when it asks me if I have a fast Internet connection...

---

### Post by teaker1s on 2007-03-31
firstly edit your sources and comment them out with [COLOR="Red"]# [/COLOR]

then
```
sudo apt-cdrom add
``` 
```
sudo apt-get update
```
then you can either dist upgrade via commandline or using synaptic

---

### Post by zvacet on 2007-03-31
Are you telling me that you tryed this
```
gksu "sh /cdrom/cdromupgrade" 
```

It works for me.

---

### Post by FireLink on 2007-03-31
> **zvacet said:**
> Are you telling me that you tryed this
```
gksu "sh /cdrom/cdromupgrade" 
```

It works for me.

It works but I do not want download anything, at least, download anything too big cause dial-up is slow...

---

### Post by FireLink on 2007-03-31
bump

---

### Post by teaker1s on 2007-03-31
you need to comment out internet sources in your sources list
```
sudo gedit /etc/apt/sources.list
```
[B]
not commented out[/B]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
**commented out[**
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

save your sources

please do as I said before then




```
sudo apt-get dist-upgrade
```

---

### Post by zvacet on 2007-04-01
You can not have upgraded version if you don´t download it.Try to download it from your friend comp or some other place with faster connection then yours.anther possibility is to wait for couple of weeks and shipit Feisty dierctly from Ubuntu.

P.S. Overlooked.It seems that you allready have alternate CD.If you don´t belive what I said disconnect your comp from net during installation.

---

