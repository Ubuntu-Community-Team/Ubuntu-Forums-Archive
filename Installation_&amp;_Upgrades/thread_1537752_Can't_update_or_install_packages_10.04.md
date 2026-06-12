---
title: "Can't update or install packages 10.04"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by seanj on 2010-07-24
EDIT: I'm sorry for not trying harder to figure this out... I chose a different mirror, one at xmission, and now can update and install. Sorry for posting prematurely.

Hi, I thought I'd give Ubuntu another shot. I had problems the last few times but forgot what they were. This one's new. I just installed 10.04 amd64 on my Core 2 Duo machine. It runs fine, but apt-get, synaptic and the update manager can't connect to the main update server or the Canadian mirror. My network is running fine though. So I can't get any of the programs I need or security updates. Not even a compiler to build an IRC client!
```
seanj@blacky:~$ sudo apt-get update
Err http://ca.archive.ubuntu.com lucid Release.gpg      
  Could not connect to ca.archive.ubuntu.com:80 (91.189.88.30). - connect (110: Connection timed out) [IP: 91.189.88.30 80]
```
```
seanj@blacky:~$ sudo apt-get update
Err http://archive.ubuntu.com lucid Release.gpg      
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (110: Connection timed out) [IP: 91.189.88.31 80]
```

---

### Post by hal8000 on 2010-07-24
Change to a different mirror. That error message shows timeout so the server is down or unreachable

---

