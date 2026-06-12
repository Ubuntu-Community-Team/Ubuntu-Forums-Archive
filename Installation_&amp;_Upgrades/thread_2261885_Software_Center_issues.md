---
title: "Software Center issues"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by Lukas_Carls on 2015-01-21
Hi all. I'm not sure if this thread belongs in a different forum, but I put it here because this issue resulted from an update. 

I updated my computer like usual on Sunday. After I rebooted, everything was fine. However, when I opened the Software Center, the app descriptions were blank, and some didn't even have anything to show. It would just say "Available through universe" or "multiverse source". Needless to say this is very inconvenient, seeing as though I can't install anything. Thanks in advance for any help!

---

### Post by ibjsb4 on 2015-01-22
Can you update in terminal and did it have any effect on the software center?
```
sudo apt-get update
```
And please post your sources list.
```
cat /etc/apt/sources.list
```

---

