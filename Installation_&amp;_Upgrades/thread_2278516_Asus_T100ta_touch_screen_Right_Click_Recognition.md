---
title: "Asus T100ta touch screen Right Click Recognition"
date: 2015-05-17
forum: Installation &amp; Upgrades
---

### Post by J_Me on 2015-05-17
Kubutu 14.04 Asus T100ta
I'm trying to get the touch screen to recognise right click. Under Input devices > Touchpad > mouse emulation things are greyed out and I get a message 'Synaptics driver is not installed (or is not used)' 
I tried installing 'xserver-xorg-input-synaptics' but it depends on 'xserver-xorg-core' So after installing 'xserver-xorg-core'/'xserver-xorg-input-synaptics' I still have the same message 'Synaptics driver is not installed (or is not used)'
How do I enable Synaptics
```
$ synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?

$ apt-cache policy xserver-xorg-input-synaptics
xserver-xorg-input-synaptics:
  Installed: 1.7.4-0ubuntu1
  Candidate: 1.7.4-0ubuntu1
  Version table:
 *** 1.7.4-0ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.15.1-0ubuntu2.7
  Candidate: 2:1.15.1-0ubuntu2.7
  Version table:
 *** 2:1.15.1-0ubuntu2.7 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2:1.15.1-0ubuntu2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```
Thanks

---

### Post by J_Me on 2015-05-26
bump

---

