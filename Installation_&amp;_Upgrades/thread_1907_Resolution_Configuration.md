---
title: "Resolution Configuration"
date: 2004-10-24
forum: Installation &amp; Upgrades
---

### Post by tor on 2004-10-24
The computer-> System Configuration -> Resolution menu only states the options 640x480, 800x600 and 1024x768. My monitor (IIyama ProLite E430) should be able to display much higher resolutions. I think the displayed resolutions are stored in the file /etc/X11/XF86Config-4... Can I just add new resoltions here (1280x1024 for example)? Or should I add these in a different way?

---

### Post by im_ka on 2004-10-24
yea you can edit it by hand or you can

```
sudo dpkg-reconfigure xserver-xfree86
```
but that'll walk you through the whole x config.

---

