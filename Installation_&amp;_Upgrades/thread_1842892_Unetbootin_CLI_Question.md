---
title: "Unetbootin CLI Question"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by cjcardinal on 2011-09-12
I did a little digging and couldn't find exactly what I was looking for, so I have come to you all for help!

Using Unetbootin to create a live USB of 10.04 Lucid, how would i go about doing what pressing "tab" at the install menu would do?

What I mean is, that for the device I am currently working on getting loaded up with 10.04, I need to tab out of the install menu to remove

```
quiet splash
```

and replace it with

```
i915.modeset=0 xforcevesa
```

Normally, I use the startupdisk creator, but for some reason with 10.04, I am having the "unknown keyword: gfxboot" issue when making a USB from the latest 10.04 ISO.  I have looked into that bug, and found the answer, via [this]("http://www.computersupportforums.com/showthread.php?tid=6901"), but my syslinux.cfg already looks as it should:

```
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
```

any guidance regarding either the Unetbootin "way" or the StartupDiskCreator way would be greatly appreciated!

Thanks in advance!

---

