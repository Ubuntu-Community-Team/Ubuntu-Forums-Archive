---
title: "without automatix"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by mr.farenheit on 2008-11-28
i've been out of the ubuntu loop for a little over a year now and came back to find that automatix was gone. so what is the quick alternative now to get a/v codecs going and some of the other apps running such as java fonts etc? i was told there was a single command for the command line that generally performed what automatix did by downloading and installing all the similar files. please point me in the right direction.

---

### Post by taurus on 2008-11-28
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mr.farenheit on 2008-11-28
i read that by uing that method you won't gain all the necessary codecs mainly the audio and basic video formats. what about for dvd and other video formats?

---

### Post by Mr. Picklesworth on 2008-11-28
If you need some restricted codecs which Ubuntu isn't allowed to officially package, check out Medibuntu. They maintain a proper debian package repository of those codecs (among other things) that are completely compatible with Ubuntu and run no risk of breaking stuff :)
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

