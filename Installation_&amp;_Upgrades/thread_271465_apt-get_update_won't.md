---
title: "apt-get update won't"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by the_flumps on 2006-10-04
Hi y'all, I just installed Dapper 6.06 and am dual booting it with winxp home. Most stuff works ok such as the internet etc, but I'm getting weirdness when I try to apt-get update, upgrade or install (this includes the update manager, and synaptic). Basically, I type in the cmd, and I get the response "Reading package lists... Done". The prog then exits back to the cmd prompt. The update manager says I'm up to date, and synaptic can't load any packages. The installation disk is about a month old, and I can't believe that I'm all up to date. Anyone got any ideas?

TIA.

---

### Post by Kateikyoushi on 2006-10-04
You could try

```
sudo apt-get clean
sudo apt-get update
```

---

### Post by the_flumps on 2006-10-04
Thanks for the response, but it had no effect.:???:

---

### Post by the_flumps on 2006-10-05
Does anyone else have any ideas I can try out?

---

### Post by linear on 2006-10-05
Try a clean sources.list? (Stick to the official repositories, though.)

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by the_flumps on 2006-10-05
You are a star! 

It hadn't even occurred to me to check the effing sources.list, and when I did I found that all the urls had been commented out during the installation (my router died during the install, and ubuntu couldn't verify the urls, so it turned them off). 

Anyway, the urls have been un-commented out, and I'm updating like a master!

Cheers!

---

