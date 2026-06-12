---
title: "Desktop not drawn correctly after upgrade to 16.10"
date: 2016-10-17
forum: Installation &amp; Upgrades
---

### Post by .Ricky. on 2016-10-17
Hello,

after upgrading to 16.10 from 16.04 I encountered an issue with my desktop (see screenshot).

[ATTACH=CONFIG]271668[/ATTACH]

Only that upper left rectangle works as a normal desktop, the rest of the screen just does not (it doesn't even respond to the right-click).

I am using Unity, and before upgrading to 16.10 on my PC I tested it on my USB (upgrading from 16.04 on there, too), and it worked fine.

One of the bug reports used to pop up, concerning compiz-core. After I submitted the report however, the message stopped appearing so I wouldn't know how to report about it here.

At first I thought it must have been some conflict between nemo and nautilus, but even after letting nautilus be the default file manager and manage my desktop the error persisted.

Oh, and the displayed wallpaper is the previous one. I changed it via the appearance settings, but it's not being changed accordingly. Unity works just fine.

What could I try?

Thanks

---

### Post by Frogs Hair on 2016-10-17
Try the following and reboot.```
sudo apt-get install dconf-tools

``` ```
dconf reset -f /org/compiz/
```

---

### Post by .Ricky. on 2016-10-18
> **Frogs Hair said:**
> Try the following and reboot.```
sudo apt-get install dconf-tools

``` ```
dconf reset -f /org/compiz/
```

Thank you for this suggestion, but doing this did not solve the problem, sadly. :neutral:

---

### Post by .Ricky. on 2016-10-18
Solved by removing nemo, using the commands

```

gsettings set org.gnome.desktop.background show-desktop-icons true
xdg-mime default nautilus.desktop inode/directory application/x-gnome-saved-search
```

and restarting nautilus.

---

