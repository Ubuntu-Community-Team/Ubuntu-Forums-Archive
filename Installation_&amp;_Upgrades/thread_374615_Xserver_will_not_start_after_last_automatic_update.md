---
title: "Xserver will not start after last automatic update"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by Don01756 on 2007-03-02
I had version 6.10 installed and all was working beautifully for 2 weeks.  Yesterday, 03/01 an automatic update was downloaded and all worked fine until PC was shut down.  Today, I am unable to boot into the OS.  Error stating X server could not be started is displayed.  Details indicate device "Screen" does not exist.  I tried running "sudo dpkg-reconfigure xserver-xorg" bot got error stating package could not be found.  Do I need to start over and reinstall the entire OS???

---

### Post by bulldog on 2007-03-02
Nope a reinstall should not be necessary.
Try to install the restricted modules for your kernel.
```
sudo aptitude install linux-restricted-modules-'uname -a'
```
Where 'uname -a' should be replaced with your kernel version.

---

### Post by Kateikyoushi on 2007-03-02
Show us how does your xorg.conf looks like.

```
cat /etc/X11/xorg.conf
```

---

