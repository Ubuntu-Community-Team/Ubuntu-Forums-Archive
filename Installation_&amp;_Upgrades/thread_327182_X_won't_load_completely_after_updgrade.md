---
title: "X won't load completely after updgrade"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by chrisg0619 on 2006-12-28
All right, I just installed 88 or so upgrades (without restarting) for Ubuntu 6.10.  In addition, I uninstalled Evolution and OpenOffice.org and reinstalled a couple of packages needed to edit the GNOME fonts and such.

Then I restarted my computer and logged in, and X won't load all the way.  I see the orange Ubuntu background, which I've changed, and nothing happens.

Any thoughts?

---

### Post by chrisg0619 on 2006-12-28
And I just realized my egregious spelling error.  Too bad I can't edit the topic title!

---

### Post by riven0 on 2006-12-28
Well, first things first; did you try reconfiguring your xserver?

> sudo dpkg-reconfigure xserver-xorg

---

### Post by chrisg0619 on 2006-12-28
Yes, I did--no luck.

---

### Post by chrisg0619 on 2006-12-28
So I ended up just installing ubuntu-desktop, and all is well.  Cheers!

---

