---
title: "Can't Create Accounts In Pidgin 2.2.2"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by rebolyte on 2007-11-18
After much pain and suffering, I have successfully compiled Pidgin 2.2.2 from source. With great anticipation I start it up, and to my great dismay there are no networks to select from the account creation drop-down menu.  Under the account creation window, the "Protocol:" drop-down shows nothing. 

Poking around, I did find this at the bottom of libpurple/libpurple.la:
```
# Directory that this library needs to be installed in:
libdir='/usr/local/lib'
```
The thing is, I can't seem to get libpurple to install into the /lib directory. It's currently just installed under pidgin-2.2.2/libpurple. What gives?

As you can imagine, Pidgin without any networks is absolutely useless, so any help would be greatly appreciated.

---

