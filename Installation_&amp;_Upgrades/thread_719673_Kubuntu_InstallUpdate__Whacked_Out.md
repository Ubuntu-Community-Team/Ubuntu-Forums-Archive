---
title: "Kubuntu Install/Update  Whacked Out"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by Nimaran on 2008-03-09
Okay, I decided to give Kubuntu a try, so I installed it from the live cd, enabled my restricted drivers, and then tried to get the large host of updates I needed, it downloaded them, but then failed when it tried to install them, then asked me if I wanted to get the 7.10 version, but wait I thought that is what I had. I said yes, but it didn't work, it would just freeze at 0% so I restarted the computer and I got no screen I could still log in via the text way, but no graphics. What should I do? Please, I need some help! :confused:

---

### Post by .nedberg on 2008-03-09
Do a ```
sudo apt-get update
```
and ```
sudo apt-get upgrade
```
It will give you an error and tell you that you need to run a command to fix it. Do that! (It is something like 'dpkg --configure -a' IIRC). Now reboot!

---

### Post by Nimaran on 2008-03-09
Thank you very much, that worked.

---

