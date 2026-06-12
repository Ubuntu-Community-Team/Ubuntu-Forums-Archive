---
title: "resolution ok with 6.06 not with 6.1"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by amazilia on 2006-10-25
Hi, 

I have a PC running with dapper with an Acer AL1715 monitor. The resolution 
is 1280x1024,75Hz.

using edgy RC2 on another machine but the same monitor I get 1024x768, 60Hz with possibilities of changing resolution.

where is the problem ?

rc2 buggy ?

thank in advance

Philippe

---

### Post by Kateikyoushi on 2006-10-25
As for me it recognised my sony and 1280*1024@75 worked out the box with pre rc1 edgy already.

You could try to reconfigure it.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by amazilia on 2006-10-25
thanks for your answer.

I only have a problem (in fact not me, but the rest of the world). How do people who do not know line commands.

It should be possible to do it through a GUI or then it is not usable...

Thanks again

Philippe

---

### Post by Kateikyoushi on 2006-10-25
Well it just starts from commandline then opens a text mode setup window.

---

### Post by amazilia on 2006-10-25
Hi,

Yes I know but most people are not even able to do that. 

Moreover there is a menu saying monitor resolution, and that does not work. it is very confusing for a normal user.

Philippe

---

### Post by Kateikyoushi on 2006-10-25
Hopefully it gets better configuration or even better autodetection so it won't be neceserry to use it, most people do not need to use it already these days.

---

