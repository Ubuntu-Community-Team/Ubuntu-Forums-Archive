---
title: "Can't install Arc theme on Ubuntu 16.04 with GNOME"
date: 2016-06-03
forum: Installation &amp; Upgrades
---

### Post by sam-pownall on 2016-06-03
I want to try out the arc theme but I am having trouble installing it. I have tried installing it manually using the git page and also downloading the binary packages directly from here: [http://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme](http://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme)
After I install I try to change the theme using the tweak tool or the unity tweak tool but it is not appearing as an option. When I look in the share/theme folder the Arc folder is not present and I receive an error message when I try to move the Arc folder into the theme section. 

How do i activate arc? 

Thank you for any help.

---

### Post by howefield on 2016-06-03
> **sam-pownall said:**
> ....When I look in the share/theme folder the Arc folder is not present and I receive an error message when I try to move the Arc folder into the theme section.

Are you using elevated rights to move the folder into the correct locatation, ie sudo ?

An idea of the error you are getting would be helpful.

---

### Post by sam-pownall on 2016-06-03
Thank you. No I wasn't so I used sudo to move the arctheme into the share/theme folder. However this did not solve the problem and I still cannot select the theme in either of the tweak tools.

---

### Post by howefield on 2016-06-03
Just to clarify, when you say *share/theme* folder, do you mean /usr/share/themes ?

---

### Post by sam-pownall on 2016-06-03
Yes, sorry. That is the folder I mean.

---

### Post by howefield on 2016-06-03
Just tested in a freshly installed and updated Ubuntu Gnome, seems to work as intended.

Downloaded the .deb package from the file in your first post, then used apt to install it.

```
sudo apt install ~/Downloads/arc-theme_1464640864.d9d1772_all.deb
```

Loaded Tweak Tool and activated the theme.

Then likewise with an icon pack.

---

