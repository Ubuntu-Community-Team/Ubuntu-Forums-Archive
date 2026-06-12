---
title: "how to install icon theme"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by Bart Ellebaut on 2007-05-23
I've downloaded a new icon theme, and I've tried to install it.
So I've extracted it, made a icon cache, but when I try to install new theme, it says not valid.
Now I've been told, I have to extract in usr/share/icons, but I do not have any permissions
what should I do

thx
Bart

---

### Post by aysiu on 2007-05-23
**Local Installation (Current User Only)**
Assuming you're using Ubuntu (and not Kubuntu or Xubuntu), go to System > Preferences > Themes. Then, take the .tar.gz (do not extract it!) and drag and drop it to the theme manager window. That's it.

**System-wide Installation (For All Users)**
Extract the .tar.gz. Press Alt-F2 and type ```
gksudo nautilus
``` In the new window navigate to /usr/share/icons. Then drag and drop the extracted folder to /usr/share/icons.

More details here:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by stchman on 2007-05-23
> **Bart Ellebaut said:**
> I've downloaded a new icon theme, and I've tried to install it.
So I've extracted it, made a icon cache, but when I try to install new theme, it says not valid.
Now I've been told, I have to extract in usr/share/icons, but I do not have any permissions
what should I do

thx
Bart

Is the icon theme still in its .tar.gz format?  Is so then you drag the compressed archive into the Themes manager.

---

### Post by myname on 2007-06-07
I am using Kubuntu, and downloaded an icon theme from kde-look.org, and am having a problem installing it.  I copied the folder to /usr/share/icons  how do I use them?

I think I need to created the icon cache file...

Any help on this?

--K

---

