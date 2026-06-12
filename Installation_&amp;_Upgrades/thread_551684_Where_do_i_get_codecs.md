---
title: "Where do i get codecs?"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by vector9 on 2007-09-15
How do i download codecs?
and which ones should i get?

---

### Post by aroch1 on 2007-09-15
That depends on what types of files you'd like it use.  Google the topic, there should be many tutorials on the web.  One useful one is [http://http://ubuntu-tutorials.com/2006/11/24/how-to-install-multimedia-codecs-ubuntu-6061-610/]("http://http://ubuntu-tutorials.com/2006/11/24/how-to-install-multimedia-codecs-ubuntu-6061-610/")

---

### Post by Pumalite on 2007-09-15
Try this at the Terminal:
sudo apt-get install ubuntu-restricted-extras

---

### Post by Crafty Kisses on 2007-09-15
> **vector9 said:**
> How do i download codecs?
and which ones should i get?

If you are talking about the Firefox and flash codecs, you can get those from the terminal. For example if you wanted to install flash you would type the following command in the terminal:
```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

---

### Post by vector9 on 2007-09-15
thanx  \\:D/ \\:D/ \\:D/

---

### Post by mindtrick on 2007-09-15
sudo apt-get install vlc 

VLC player plays almost every video file without the need of external codecs.

---

### Post by linuxwizard on 2007-09-15
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

