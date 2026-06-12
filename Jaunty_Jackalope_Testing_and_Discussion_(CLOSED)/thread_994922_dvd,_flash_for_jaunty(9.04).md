---
title: "dvd, flash for jaunty(9.04)"
date: 2008-11-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by luceerose on 2008-11-27
I have already installed Totem-Xine & Amarok-Xine.

I want to install;
Flash
&
DVD playback

for Jaunty Jackalope (9.04a) AMD64
Has anyone figured out how to do this yet ?

EDIT: BTW, I thought I would mention that the medibuntu repository for jaunty actually works.

---

### Post by luceerose on 2008-11-27
OK, as per H4rold's instructions in this post: [http://ubuntuforums.org/showpost.php?p=6196594&postcount=451](http://ubuntuforums.org/showpost.php?p=6196594&postcount=451)

I did this;
```

apt-get --purge remove nonfree-flashplugin nspluginwrapper

wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)

tar xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz

sudo mv libflashplayer.so /usr/lib/mozilla/plugins/

```

That got flash installed beautifully. Actually one of the quickest & easiest flash installs I've done on any version of ubuntu. Works flawlessly, too.

Still need DVD playback.
Any Ideas ???

---

### Post by kusuriya on 2008-12-21
Im sure its a bit old but for search sake,

you can add the medibuntu repository (the intrepid index for it works fine)
just follow the instructions at [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories"), and install the K/X/Ubuntu-restricted-extras (pick your poison), and that should give you all of your DVD, Flash, MP3, AAC, and E-Penis bragging rights back.

---

### Post by LordVeovis on 2008-12-21
> **kusuriya said:**
> Im sure its a bit old but for search sake,

you can add the medibuntu repository (the intrepid index for it works fine)
just follow the instructions at [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories"), and install the K/X/Ubuntu-restricted-extras (pick your poison), and that should give you all of your DVD, Flash, MP3, AAC, and E-Penis bragging rights back.

Worked for me.  My E-peen is big again.

---

