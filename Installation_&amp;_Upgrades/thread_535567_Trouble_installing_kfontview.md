---
title: "Trouble installing kfontview"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by Niscrome on 2007-08-26
Hi,
This problem started when I wanted to install fonts from the internet. I had tried to drag the fonts to the font folder but that didn't work. So I try to  install Kfontview and all I get is an error. 
Can someone please help me!? Here is the error I get...

```
randompat@ubuntu:~$  apt-get install kcontrol
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

Little more info:
I have an external harddrive ( I believe the "E:" maybe the external)
I am also using Wubi

---

### Post by kellemes on 2007-08-26
should be "**sudo** apt-get install kcontrol"

---

### Post by Niscrome on 2007-08-26
Thanks Dude that really solve the problem...Linux is a whole new learning process from XP. I love linux! And thank you once again!:biggrin:

---

