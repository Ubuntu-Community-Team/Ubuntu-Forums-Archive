---
title: "Dapper-&gt;Edgy nvidia GLX problem"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by muxecoid on 2006-10-28
After the upgrade OpenGL apps stopped working, nvidia-settings says
> The OpenGL extension 'GLX' is not supported by
the X server or there was a problem retrieving
GLX information from the X server.

If I try to enable
```
muxecoid@muxecoid-desktop:~$ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
```

WTF? WMBD?

---

### Post by dinoc on 2006-10-28
Yes I have the very same issues with a lot of X (using OpenGl GLX with nvidia driver) applications after upgrading fro 6.0.6LT to 6.10.
For instant blender, torcs ... and others, used to work fine on 6.0.6, but now on 6.10 they don't work ... the error is the same one reported in previous post.
I used to use nvidia_legacy drivers.

---

### Post by muxecoid on 2006-10-28
How did you solve it?

---

### Post by sblanzio on 2006-10-29
same problems. please find some fix!!

thanks!

---

### Post by sblanzio on 2006-10-29
I found this workaround [here]("http://www.ubuntuforums.org/showpost.php?p=1575868&postcount=5") that worked perfectly with me:

> 

type:
```

sudo nano -w /etc/X11/xorg.conf

```

get to the end of the file (using your keyboard arrows) and add this:
```

Section "Extensions" 
Option "Composite" "Disable" EndSection

```
then press CTRL+X to exit (save the file)



```
sudo reboot
```

i hope this helps

---

### Post by gnudownload on 2006-10-31
thanks sblanzio :-D

---

