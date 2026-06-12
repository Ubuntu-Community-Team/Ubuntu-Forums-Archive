---
title: "Beryl on new ATI drivers..anybody?"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by madu on 2007-08-22
Hi guys...

I want to install Beryl on my Lenovo T60 laptop.. which has an ATI X1400 vid card.. 
I followed the following link:
[http://cyberkruz.vox.com/library/post/installing-ubuntu-on-t60-with-xgl-and-beryl.html]("http://cyberkruz.vox.com/library/post/installing-ubuntu-on-t60-with-xgl-and-beryl.html")

But I stuck at:
> emerald-themes xserver-xgl
which gives me:
> emerald-themes: command not found

If anybody got any idea or a guide, much appreciated.

Thank you.

Madu.

---

### Post by mocoloco on 2007-08-22
This should all be on one line
```

sudo apt-get install beryl beryl-core beryl-plugins beryl-plugins-data beryl-settings beryl-manager emerald emerald-themes xserver-xgl
```

Or I'm guessing you installed just the one line, in which case you just need to do:

```
sudo apt-get install emerald-themes xserver-xgl
```

---

