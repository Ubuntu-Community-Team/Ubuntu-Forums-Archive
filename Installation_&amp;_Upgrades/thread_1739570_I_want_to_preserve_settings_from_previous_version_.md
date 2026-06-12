---
title: "I want to preserve settings from previous version of ubuntu"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by adit on 2011-04-26
I am now using ubuntu 10.10.  I am going to install ubuntu 11.04 on April 28 (after it is released).  I want to preserve:
1) the list of extra programs installed by me on ubuntu 10.10 (I want to install the same programs in 11.04 also)
2) program settings

My questions:
1) From synaptic package manager menu:
File -> Save Markings (save full state, not only changes)
saves in a text file the list of programs installed on my system. I used that file to install the same programs in several computers running ubuntu 10.10.  Is there a way to use that list in 11.04 also.

2) Copying the directory ~/.mozilla preserves all settings of firefox from previous installation.  Like that what files should be copied for gnome applications (gnome-panel, nautilus, etc.)

I know preserving settings 100% is impossible.  I want to preserve as much as possible.  Advice me what to do.  I want to do a clean installation.  I don't want to do upgrade, because upgrade usually results in a major problem like inability to boot.

---

### Post by mörgæs on 2011-04-26
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by Pand5461 on 2011-04-26
I think most of user preferences are stored in hidden files/folders in home directory. You can backup them by
```
cp -r ~/.* destination
```

---

