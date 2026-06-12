---
title: "Installing 11.04 on laptop with two screens"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by toscroll on 2011-06-14
I want to install and use 11.04 64bit on my laptop.My laptop's matrix is broken so i connected another monitor for it to work.Everything was fine untill i updated to 11.04 from 10.04.After installing and turning on laptop, it loaded unity, and my monitor didnt turn on.Becouse my laptop main screen isnt working i cant check for screen or look for preferences to change.Any ideas?

---

### Post by MAFoElffen on 2011-06-15
> **toscroll said:**
> I want to install and use 11.04 64bit on my laptop.My laptop's matrix is broken so i connected another monitor for it to work.Everything was fine untill i updated to 11.04 from 10.04.After installing and turning on laptop, it loaded unity, and my monitor didnt turn on.Becouse my laptop main screen isnt working i cant check for screen or look for preferences to change.Any ideas?
What video chipset does your laptop have?  What I'm thinking is that you would need to edit your /etc/X11/xorg.conf to force your laptop's display off and to force output to the your external port...  If there is no xorg.conf present, you could create one to do it.

If you can get to your /etc/X11/xorg.conf... Please post.  Remember to use the " # " icon of the forum posting bar and paste the text of the file within the CODE tags.

---

### Post by toscroll on 2011-06-16
> **MAFoElffen said:**
> What video chipset does your laptop have?  What I'm thinking is that you would need to edit your /etc/X11/xorg.conf to force your laptop's display off and to force output to the your external port...  If there is no xorg.conf present, you could create one to do it.

If you can get to your /etc/X11/xorg.conf... Please post.  Remember to use the " # " icon of the forum posting bar and paste the text of the file within the CODE tags.

Its Nvidia.Also i somehow managed to get to that file, here is the code:
```
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```

---

