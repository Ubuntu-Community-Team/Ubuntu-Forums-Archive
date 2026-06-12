---
title: "Cannot install Flash plugin for Firefox"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by utahan on 2008-10-30
Ever since I loaded Hardy Heron with Firefox 3.0 I have not been able to get the Flash plugin to work...either by plugin or manually download and install.  I've heard somewhere that it's not a priority for Adobe but it did work on Firefox 2.x.  This is really aggravating.  Anybody else having this problem and what did you do?

Thanks ahead of time.

---

### Post by martrn on 2008-10-30
I think the answer is seperate for 32bit systems from the 64bit ubuntu systems.  On a 32bit system you can:

```
sudo apt-get install flashplugin-nonfree
```

On a 64bit ubuntu system there is no 64bit flash and while there is no 'official' solution the 'work around' is here:

[URL="http://ubuntuforums.org/showthread.php?t=476924"]
http://ubuntuforums.org/showthread.php?t=476924[/URL]

and for firefox3 its:
[URL="http://ubuntuforums.org/showthread.php?t=695674"]
http://ubuntuforums.org/showthread.php?t=695674[/URL]

It works, if you follow this.

---

