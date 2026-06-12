---
title: "Added a 2TB Hitachi hard drive, but can't write to it..."
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by jaime256 on 2009-12-31
Okay, I just added a 2 Terabyte Hitachi hard drive through the USB to back up some stuff. Unfortunately Ubuntu 9.04 won't let me write to it. I have created a primaray and then I did a logical but both give me the same results.

---

### Post by drs305 on 2009-12-31
The presence of the 'lost+found' folder means it's formatted and recognized. It's probably a permission problem - the mountpoint is most likely still owned by root.

I just posted this a few hours ago. You could repeat the steps. Making the mountpoint and creating an fstab entry isn't really necessary if it automounts to the same location each time. 

[http://ubuntuforums.org/showthread.php?t=1368890]("http://ubuntuforums.org/showthread.php?t=1368890")
Post #6

---

### Post by jaime256 on 2009-12-31
Thanks I'm pretty sure it has something to do with the rigths too. I'll take a look at your other thread. Well, I don't want mess with files much so I tried, **sudo nautilus** and this allows me to use it. Ugly, but seems to work quicker than playing with files.

Okay, I can add folders but I can't drop files from the nas into the folders. So I gotta figure another way to back this up.

---

