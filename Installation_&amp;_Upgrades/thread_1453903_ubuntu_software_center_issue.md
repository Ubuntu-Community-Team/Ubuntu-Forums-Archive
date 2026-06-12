---
title: "ubuntu software center issue"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by us11csalyer on 2010-04-13
I can't open ubuntu software center.

Error:
stephen@stephen-desktop:/usr/bin$ software-center
Segmentation fault
stephen@stephen-desktop:/usr/bin$ 

I tried the following commands:

sudo apt-get purge software-center
sudo apt-get install software-center

Both of the commands above did not produce any errors; however, I still get the same error when trying to start ubuntu software center.

---

### Post by plucky on 2010-04-14
> **us11csalyer said:**
> I can't open ubuntu software center.

Error:
stephen@stephen-desktop:/usr/bin$ software-center
Segmentation fault
stephen@stephen-desktop:/usr/bin$ 

I tried the following commands:

sudo apt-get purge software-center
sudo apt-get install software-center

Both of the commands above did not produce any errors; however, I still get the same error when trying to start ubuntu software center.

Try ```
sudo apt-get clean
sudo apt-get install --reinstall software-center
```
the clean command will clear out the archives files,so if you want to keep them,don't run the commands.

It will then have to download the files again to install.

Good Luck

---

