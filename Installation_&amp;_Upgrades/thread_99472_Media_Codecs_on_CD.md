---
title: "Media Codecs on CD?"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by Debrihmi on 2005-12-05
Hello there..
How do I download media codecs onto a CD for install on non-internet connected PCs?
~
Debrihmi

---

### Post by tseliot on 2005-12-05
you can go there [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/non-free/w32codecs/]("ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/non-free/w32codecs/") and download "w32codecs_20050412-1plf4_i386.deb".

Then copy this file to the other pc. 
Open Terminal and get to the directory where you put that file and type:
```
sudo dpkg -i w32codecs_20050412-1plf4_i386.deb
```

and the codecs will be installed

---

### Post by bored2k on 2005-12-05
Doing this might be considered illegal on some countries. Thread locked.

---

