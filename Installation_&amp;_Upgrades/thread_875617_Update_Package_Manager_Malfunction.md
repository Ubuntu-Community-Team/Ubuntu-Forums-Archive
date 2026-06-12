---
title: "Update Package Manager Malfunction"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by CGS_Saltire on 2008-07-31
Hi All,
 I have a problem with my update package manager. Two days ago I used Transmission to download a torrent and when it was complete shut the program down and went to bed leaving Ubuntu to go to screen saver. At that time it was displaying the little sun icon with 10 updates left, but next morning when I checked my computer it had changed to the red arrow head. Since my computer uses Gnome PPP to access the internet this was also shut down over night. 

Highlighting the red arrow showed that there was one update available but when I clicked on it and started the update manager it showed 89 updates. I selected the most important updates relating to security and others hoping that it would sort it's self out but when it finished and I rebooted Ubuntu as required I still had the same red arrow but this time it was showing 3 updates. This is despite their being 29 left! I don't understand why it has suddenly gone haywire like this! Anyone have any ideas on what has happened and how to fix it?
CGS_Saltire

---

### Post by SkonesMickLoud on 2008-07-31
Try:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by CGS_Saltire on 2008-07-31
Thanks for the info! Hopefully it works first time.

CGS_Saltire

---

### Post by CGS_Saltire on 2008-07-31
Your code is still working in my terminal so until it finishes I won't know if it is completely successful or not. Just wondering do you know why it did this? I am relatively new to Linux though I have had Ubuntu since Edgy was released. 

CGS_Saltire

---

### Post by CGS_Saltire on 2008-07-31
My terminal just finished executing the code you supplied me with! Many thanks again! :)  It worked perfectly! :) There are still two updates remaining but they are not critical ones! And again I have the little sun icon with the small arrow in it being displayed! :KS

CGS_Saltire

---

### Post by SkonesMickLoud on 2008-07-31
> **CGS_Saltire said:**
> Just wondering do you know why it did this?

Dunno.  Stuff just happens sometimes.

Your list of packages probably wasn't updated.  Anytime you go more than a few days without using 'apt-get' or 'aptitude' it's a good idea to run:

```
sudo aptitude (or apt-get) update
```

---

### Post by CGS_Saltire on 2008-08-02
Yeah! I know what you mean! Usually at the wrong time too! I noticed yesterday that after running your code and straightening out the package manager that a day later there were package manager updates waiting to be installed. At the moment Hardy is working brilliantly again and I have no complaints with it. It's up to date (Almost! ...I have Mozilla NVU installed and don't wish to exchange it for Komposer!)running rings around my copy of windows! Yeah! My computer is dual boot! Hopefully with my next hardware upgrade that will end!
CGS_Saltire

---

