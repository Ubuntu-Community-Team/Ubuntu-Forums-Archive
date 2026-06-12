---
title: "Installer Doesn't Recognize SATA RAID"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by HomerSimpson748 on 2008-04-16
The Ubuntu installer isn't recognizing my mirrored SATA RAID. It's recognizing both drives - not the array. My gparted live cd recognizes the array just fine.

I'm stumped. Can anyone help?

---

### Post by st0nedpenguin on 2008-04-16
If you're running onboard RAID, this might come in handy:

[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation](http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation)

There's a fair bit of fiddling installed but it got Gutsy up and running on my nvraid without a hitch.

(Guide was linked from [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) which also has more info)

---

### Post by mk4umha on 2008-06-17
If you have windows that accesses that raid, will dmraid be able to see the same paritions without having to redo the drives? I dont want to lose data and i'd like to share the raid setup between both OS's.

---

