---
title: "Last ubuntu update failed (13/10/2016)"
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by Carlo_Mangiarulo on 2016-10-14
Hi everybody, 
I'm new on this forum, I'm an Italian user and I prefer sometimes use a forum in italian language. 
 
But I'm not here to discussing about that. As the title, yesterday  evening I installed the last update (sorry I don't remember the name,  but I think that was about 500KB ).
After installation, Is not working anymore, wireless card, usb ports, hdmi ports.

Someone will be so kind to help me to fix this problem?

Thanks a lot and sorry for may English (if is not good :razz:)

---

### Post by howefield on 2016-10-14
> **Carlo_Mangiarulo said:**
> I'm new on this forum, I'm an Italian user and I prefer sometimes use a forum in italian language. 

[http://forum.ubuntu-it.org/](http://forum.ubuntu-it.org/)
 
> ....yesterday  evening I installed the last update (sorry I don't remember the name,  but I think that was about 500KB ).

Open the apt history.log file in a text editor and post the information about the last update(s) that you applied.

```
/var/log/apt/history.log
```

---

### Post by Carlo_Mangiarulo on 2016-10-14
Thank you howefield, I know that exist an italian forum but sometimes is not helpful.

Anyway, I can't copy and cut here the output because are not working USBs, LAN and so on. I'm using another pc to write here.

the output of **last** update after the command ```
 /var/log/apt/history.log 
``` is:

```
Start-Date 2016-10-13 22:39:22
Commandline: aptdaemon role='role-commit-packages' sender=':1.110'
Install: linux-signed-image-4.4.0-43-generic:amd64 (4.4.0-43.63, automatic), linux-image-4.4.0-43-generic:amd64 (4.4.0-43.63, automatic)
Upgrade: libdbusmenu-glib4:amd64 (12.10.3+16.04.20160223.1-0ubuntu1, 16.04.1+16.04.20160927-0ubuntu1), libdbusmenu-gtk4:amd (12.10.3+16.04.20160223.1-0ubuntu1, 16.04.1+16.04.20160927-0ubuntu1), kbd:amd64 (1.15.5-1ubuntu4, 1.15.5-1ubuntu5), libappstream-glib8:amd64 (0.5.13-1ubuntu3, 0.5.13-1ubuntu4), gir1.2-dbusmenu-glib-0.4:amd64 (12.10.3+16.04.20160223.1-0ubuntu1, 16.04.1+16.04.20160927-0ubuntu1), libdbusmenu-gtk3-4:amd64 (12.10.3+16.04.20160223.1-0ubuntu1, 16.04.1+16.04.20160927-0ubuntu1), lightdm:amd64 (1.18.2-0ubuntu2, 1.18.3-0ubuntu1), liblightdm-gobject-1-0:amd64 (1.18.2-0ubuntu2, 1.18.3-0ubuntu1)
End-Date: 2016-10-13 22:40:21
```

Thanks again [COLOR=#DD4814][COLOR=#DD4814][[COLOR=#990303]howefield[/COLOR]]("https://ubuntuforums.org/member.php?u=186490")[/COLOR][/COLOR][COLOR=#DD4814][COLOR=#990303][/COLOR][/COLOR]

---

### Post by howefield on 2016-10-14
I see a kernel version *-43 in there, there was a another kernel update that came very shortly after that, *-44. I'd suggest updating again and hopefully you will get the latest kernel, if that doesn't work, try booting via the last "good" kernel.

---

### Post by Carlo_Mangiarulo on 2016-10-14
Thanks [COLOR=#000000]howefield, I solved booting the sistem to the previous kernel.[/COLOR]

---

### Post by Carlo_Mangiarulo on 2016-10-14
I forgot to put SOLVE on the title [CENTER][COLOR=#000000]\\:D/[/COLOR][/CENTER]

---

### Post by howefield on 2016-10-14
Cool, hopefully when you get the newest kernel you won't have the issue :)

---

