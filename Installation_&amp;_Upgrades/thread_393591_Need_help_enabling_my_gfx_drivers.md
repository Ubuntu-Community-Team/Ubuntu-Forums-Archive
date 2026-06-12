---
title: "Need help enabling my gfx drivers"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by titan3169 on 2007-03-25
i was wondering how to enable my gfx drivers. i keep getting this when ever i put in the command. 

jp@Jp-D:~$ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
jp@Jp-D:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied

thx for the help

---

### Post by Waappu on 2007-03-26
Hi

Use envy to install driver and let it configure your xorg.conf
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by titan3169 on 2007-03-26
thx ill try that when i get hom from school

---

### Post by Waappu on 2007-03-26
Hi

And if you want edit xorg.conf type this to terminal ```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by titan3169 on 2007-03-26
When typed "/etc/X11/xorg.conf" it said my permission was denied. Do i need to add the "gksudo gedit" to make it work?

---

### Post by Waappu on 2007-03-26
Hi

Yes.

```
gksudo
``` means that you want execute as root ```
gedit
```means you want open text editor```
/etc/X11/xorg.conf
```is file that you want to open as root in text editor=)

---

### Post by titan3169 on 2007-03-26
it will probably work now. :) thx for the help. im a newbie ;)

---

### Post by Waappu on 2007-03-26
Hi

I think you get best result if you use envy.

---

### Post by titan3169 on 2007-03-26
k ill try that out.

---

