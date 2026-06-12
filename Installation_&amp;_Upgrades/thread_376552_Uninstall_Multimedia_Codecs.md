---
title: "Uninstall Multimedia Codecs?"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by Sand Lee on 2007-03-05
I seem to have downloaded some illegal codecs *cough cough* using the directions from [[COLOR="Blue"]_wordpress_[/COLOR]]("http://linux.wordpress.com/2006/06/13/ubuntu-one-command-to-have-all-multimedia-working/"). In trying to be the good US citizen that i am, can anyone tell me how to remove the illegal codecs? :KS

---

### Post by tubasoldier on 2007-03-05
```
sudo aptitude remove gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly libdvdcss w32codecs
```

There may be more but that will stop you from watching the DVDs that you purchased and listening to the music you bought.

---

### Post by Sand Lee on 2007-03-05
Thank you for making me a better person!! :lolflag:

---

