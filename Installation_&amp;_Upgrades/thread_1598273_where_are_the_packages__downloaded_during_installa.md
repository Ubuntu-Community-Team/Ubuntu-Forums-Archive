---
title: "where are the packages  downloaded during installation"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by metricspace on 2010-10-16
Hi there, 

Recently I installed  airlines-themes, using the command 
```
sudo aptitude install airlines-theme
```It worked perfectly. My question is where are all these packages downloaded locally, so that if needed I can install them later without an Internet connection.

Not just theme, I can do it for other application as well (for eg. ubuntu tweak and many others).

Thanks,
metric

---

### Post by Rocket2DMn on 2010-10-16
Deb files are downloaded to /var/cache/apt/archives/

If you are going to copy them elsewhere, make sure you have any dependencies that you will need as well.

---

### Post by metricspace on 2010-10-16
thank you very very much.

found all the deb files in the folder you mentioned, including **airlines-theme_1.4.1.lucid.ppa1_all.deb**. However for VLC there were multiple files like vlc_1.0.6-1ubuntu1.2_i386.deb, vlc-data_1.0.6-1ubuntu1.2_all.deb, as mentioned they must be dependent files.

I don't know from where to download the .deb files so that I can install them offline, for pidgin I tried and reached 
[http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/](http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/) however couldn't make out which file to download. 

Yes I can install it  from [http://appnr.com/](http://appnr.com/), however want to how can I  download it's deb package, so that I can install it later locally or install it on other PC running ubuntu. (copying .deb files from /var/.... folder is one way that I've just learned)

Thank you once again for the guide,
metric

---

### Post by sikander3786 on 2010-10-16
Keryx is always helpful for offline installations.

[http://keryxproject.org/](http://keryxproject.org/)

You can download all the packages from

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

But it is always a hassle to download all the dependencies therefore making it hard as in the case you mentioned,

> vlc_1.0.6-1ubuntu1.2_i386.deb, vlc-data_1.0.6-1ubuntu1.2_all.de

---

### Post by Rocket2DMn on 2010-10-16
I'm not sure how up to date this page is, but there are multiple ways of getting packages between computers.  Have a look at [https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline).

Also note that the Ubuntu alternate install CD can be used as a CD-ROM repository. I think the LiveCD may also work these days.

---

### Post by metricspace on 2010-10-16
Thank you once again for the help.

---

