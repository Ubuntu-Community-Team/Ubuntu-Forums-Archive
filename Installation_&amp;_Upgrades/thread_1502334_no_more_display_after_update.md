---
title: "no more display after update"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by junkone on 2010-06-05
i updated Ubuntu and do not get any more display. when i bootup , i can see the ubuntu flash in middle of the screen for 1 sec and everything disappears.
dunno what to do.

---

### Post by kansasnoob on 2010-06-05
Post the output of:

```
lspci | grep VGA
```

That will display the specific graphics chip info.

---

### Post by junkone on 2010-06-05
thanks for your response. here is the output.

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)

how do i fix it?

i went to grub and logged in thro a earlier version. on may30, i had updated the following. i checked the synaptic version history.

Upgraded the following packages:
chromium-browser (6.0.414.0~svn20100523r47994-0ubuntu1~ucd1~jaunty) to 6.0.419.0~svn20100528r48457-0ubuntu1~ucd1~jaunty
chromium-browser-inspector (6.0.414.0~svn20100523r47994-0ubuntu1~ucd1~jaunty) to 6.0.419.0~svn20100528r48457-0ubuntu1~ucd1~jaunty
chromium-codecs-ffmpeg (0.5+svn20100522r47988+47943+47971-0ubuntu1~ucd1~jaunty) to 0.5+svn20100522r47988+47943+48395-0ubuntu1~ucd1~jaunty
libc-bin (2.10.1-0ubuntu16) to 2.10.1-0ubuntu17
libc-dev-bin (2.10.1-0ubuntu16) to 2.10.1-0ubuntu17
libc6 (2.10.1-0ubuntu16) to 2.10.1-0ubuntu17
libc6-dev (2.10.1-0ubuntu16) to 2.10.1-0ubuntu17
libc6-i686 (2.10.1-0ubuntu16) to 2.10.1-0ubuntu17
libvpx0 (0.9.0-3~ucd1~jaunty) to 0.9.0-4~ucd1~jaunty

---

