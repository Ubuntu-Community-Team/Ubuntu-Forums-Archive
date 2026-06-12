---
title: "package update hangs"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by DouglasAdams on 2010-02-22
after doing:
 $ sudo apt-get update

i get lots of hits then:
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources
 99% [Waiting for headers]

... and it just sits there.

a reload in synaptic gives:
 downloading file 44 of 45

... and it just sits there.

when i abort i get the following shown in error message:
 Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_GB.bz2](http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_GB.bz2)  
 Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  
 Some index files failed to download, they have been ignored, or old ones used instead.

i'm still new to ubuntu so i really didn't expect this ...

---

### Post by slakkie on 2010-02-22
I've had the same problem on several boxes.

Remove or comment out the soures in /etc/apt/sources.list.d/google-chrome.list (or something similar).

When you have done that, no more issues :)

---

### Post by DouglasAdams on 2010-02-22
google chrome is currently my fav browser,
is thst still ok slakkie?

---

### Post by RJARRRPCGP on 2010-02-22
> **DouglasAdams said:**
> 

when i abort i get the following shown in error message:
 Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_GB.bz2](http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_GB.bz2)  


This link returns: 

Google   	 

     Error
 

    Not Found
    The requested URL /linux/deb/dists/stable/main/i18n/Translation-en_GB.bz2 was not found on this server.

---

### Post by DouglasAdams on 2010-02-22
cheers guys
RESOLVED
... i will close the thread

---

### Post by slakkie on 2010-02-22
> **DouglasAdams said:**
> google chrome is currently my fav browser,
is thst still ok slakkie?

Yes, you won't be able to upgrade chrome anymore but at least you can keep the rest of your system OK :) You can still use chrome.

---

### Post by DouglasAdams on 2010-02-22
does anyone have the address at google to thank them for removing the files that everyone needs please?

---

### Post by cstring on 2010-03-12
Thanks, this worked great for me!

---

