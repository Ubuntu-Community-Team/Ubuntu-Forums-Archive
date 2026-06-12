---
title: "Pidgin  update"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by kid1000002000 on 2011-01-04
I subscribe to the latest pidgin ppa and get this error when performing a synaptic update:

E: /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.10_all.deb: trying to overwrite '/usr/share/pixmaps/pidgin/protocols/16/facebook.png', which is also in package pidgin-facebookchat 1.67.1-1


Is this a bug, or something wrong with my computer?  I have tried removing and reinstalling everything pidgin related.

---

### Post by shrijith1 on 2011-01-04
same with me too :(

---

### Post by kiddykoff on 2011-01-06
E: /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.10_all.deb: trying to overwrite '/usr/share/pixmaps/pidgin/protocols/16/facebook.png', which is also in package pidgin-facebookchat 1.67.1-1

same here, i tried
```
sudo rm /usr/share/pixmaps/pidgin/protocols/16/facebook.png
``` but it doesn't work.

I just tried
```
sudo apt-get remove pidgin
sudo apt-get install pidgin
```

i'm thinking it will do the trick

---

### Post by kiddykoff on 2011-01-06
it worked for me.

---

