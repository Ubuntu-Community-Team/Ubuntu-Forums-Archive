---
title: "how to install intel video driver?"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by Timmy0829 on 2013-06-18
I have this video card:

Intel Corporation Ivy Bridge GraphicsController (rev 09)

But I dont really think its working correctly. How can I install the proper driver? The additional driver shows only the wifi driver nothing else.

Thanks

---

### Post by papibe on 2013-06-18
Hi Timmy0829.

The proper one would be the Intel driver that comes preinstalled on Ubuntu. If you want to know which one is in used run this:
```
lspci -nnk | grep -iA2 vga
```

What kind of problems are you experiencing?

I don't think installing another driver would help, but you may want to choose to upgrade to a more recent version (with the slightly risk of stability issues).

Let us know how it goes.
Regards.

---

### Post by Timmy0829 on 2013-06-18
I was trying to install compiz and every time I appied the cube for example something went wrong. Was very slowly, freezing and etc...

I thought my video driver is not up to date.

---

### Post by papibe on 2013-06-18
Take a look at this guide: [Composite Manager]("https://help.ubuntu.com/community/CompositeManager"). 

There may be more details and discussion here: [Cube and Desktop Effects in Compiz]("http://ubuntuforums.org/showthread.php?t=1892851").

Regards.

---

