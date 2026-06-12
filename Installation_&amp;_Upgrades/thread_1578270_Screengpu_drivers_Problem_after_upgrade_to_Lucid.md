---
title: "Screen/gpu drivers Problem after upgrade to Lucid"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by dll0r on 2010-09-20
after upgrade to lucid my screen gets wavy after a short amount of time, i install the official nvidia linux drivers but the problem is still there..

i attach an image to see what i mean

Tnx in advance

Spyros

[IMG]http://img84.imageshack.us/img84/5372/screenshotyvz.png[/IMG]

---

### Post by vishnu.prathap on 2010-09-21
hey, 
   I had the same problem with lucid. 
I installed the driver, downloaded from nVidia's site.

To get more clear, this is what I did.

Download the driver from nVidia's site and do the following.

go to console mode. (Ctrl + Alt + F1)
```

sudo /etc/init.d/gdm stop
cd <DRIVER_DIRECTORY>
chmod +x <driver>
sudo ./<driver>
sudo /etc/init.d/gdm start

```

And a reboot solved it. Hope it helped.

---

