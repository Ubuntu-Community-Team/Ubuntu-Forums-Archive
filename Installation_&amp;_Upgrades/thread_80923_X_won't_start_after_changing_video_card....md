---
title: "X won't start after changing video card..."
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by BinaryDigit on 2005-10-23
Hi all,
Not sure if I'm posting this in the right forum, but how do I re-install or correct X? I changed out my video card from an Nvidia to an ATI (The nvidia was dying).  Now I can't start X :(
Any help would be much appreciated :D

:KSBit

---

### Post by Koybe on 2005-10-23
On debian i would say
```
sudo dpkg-reconfigure xserver-xorg
```

I don't know if it will work on ubuntu, give it a try.

---

### Post by BinaryDigit on 2005-10-24
Ok I'll try that, thanks :)

---

### Post by BinaryDigit on 2005-10-25
[QUOTE=Koybe]On debian i would say
```
sudo dpkg-reconfigure xserver-xorg
```

I don't know if it will work on ubuntu, give it a try.[/QUOTE]
This worked!!! Thank you sooooo much!!!!!

---

