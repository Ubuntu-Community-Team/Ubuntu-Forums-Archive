---
title: "im stupid, tell me what to do"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by zeu on 2005-04-08
how EXACTLY do i upgrade to hoary?

i heard something about changing from woary to hoary in synaptic and then doing a dist-upgrade but i forgot how it was done.

please tell me and thanks in advance :)

---

### Post by dusu on 2005-04-08
Hi,

you first have to edit your /etc/apt/sources.list file and make it look like it's given in 
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

Then do 
```
sudo apt-get update
sudo apt-get upgrade
```

For any more infos, please read [http://ubuntuguide.org/](http://ubuntuguide.org/) and [http://ubuntuguide.org/4.10/index.html](http://ubuntuguide.org/4.10/index.html)

---

### Post by az on 2005-04-08
You can just use synaptic and change the repository information.  Select each one that is active and change the word Warty to Hoary.

Then refresh and do a smart upgrade.

---

### Post by zeu on 2005-04-08
[QUOTE=azz]You can just use synaptic and change the repository information.  Select each one that is active and change the word Warty to Hoary.

Then refresh and do a smart upgrade.[/QUOTE]
 thank you all, its now upgrading and its taking a HELL of a long time, but the thought of e17 makes it all worth it.. :D

---

