---
title: "I can't start ubuntu server without a display crad"
date: 2017-11-08
forum: Installation &amp; Upgrades
---

### Post by james616616 on 2017-11-08
I am using intel E3-1230v3 as the CPU which had no build-in display, 
using an display card to install and config the ubuntu server , it works normally so far.

After I shutdown ,remove that display card , and power-on again,
I cannot connect to it via ssh,samba,nginx, or what ever the server runs .
Then I put the display card back in it ,and it works normally again.

Is there a config to allow the ubuntu server starts without display?

---

### Post by deadflowr on 2017-11-08
i believe you need to install the dummy xorg package
```
sudo apt-get install xserver-xorg-video-dummy
```

Something something more on that here:
[https://ubuntuforums.org/showthread.php?t=1832456]("https://ubuntuforums.org/showthread.php?t=1832456")

---

