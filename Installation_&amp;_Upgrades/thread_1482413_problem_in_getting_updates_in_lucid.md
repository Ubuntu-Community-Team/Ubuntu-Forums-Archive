---
title: "problem in getting updates in lucid"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by sunphilic on 2010-05-13
i use synaptic manager to get the updates. I tried to get the required plugins like gstreamer 0.10 plugins bad. I downloads the all the required files but at last it show the following 

E: Internal Error, Could not perform immediate configuration (2) on mountall

can any body help how to install these updates plz

---

### Post by mörgæs on 2010-05-14
If you try upgrading this way on a freshly booted machine:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

in stead of using Synaptic, what happens?

---

