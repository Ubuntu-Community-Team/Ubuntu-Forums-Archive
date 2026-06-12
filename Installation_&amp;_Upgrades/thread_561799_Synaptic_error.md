---
title: "Synaptic error"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by mayurarora on 2007-09-28
I recently downloaded a debian package from getdeb.net named SECONDLIFE.While installing it with Gdebi Package installer I came to know that it would further download about 50 mbs.I stopped its installation immediately and it hung.Now whenever i try to open synaptic it gives me an error message
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
I have figured out that I cannot even use update manager or Add/remove Programs.
I donot wish to install Secondlife.Is there any solution?

---

### Post by aJayRoo on 2007-09-28
Try performing a system update from the command line:
```
sudo apt-get update
sudo apt-get upgrade
```
This is likely to give you a more productive error message. Usually the error message will contain a command to fix the problem. If you are unsure of how to proceed then post any error messages here and I'm sure some one can help.

---

### Post by Pumalite on 2007-09-28
Run:
sudo dpkg --configure -a

---

