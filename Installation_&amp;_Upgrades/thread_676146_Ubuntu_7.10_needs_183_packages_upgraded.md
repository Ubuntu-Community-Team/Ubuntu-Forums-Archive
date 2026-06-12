---
title: "Ubuntu 7.10 needs 183 packages upgraded?"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by John_W on 2008-01-23
I did a fresh install of Ubuntu 7.10.
System is running fine but the update manager shows there are 183 updates available.
I'm hesitant to install the 183 updates because the summary window warns **"You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system."** I'll attach a screen shot of the warning. Is it safe to run the updates of leave the system alone since it's running fine.

---

### Post by forestpixie on 2008-01-23
generally the can't be authenticated message refers to software not supplied by ubuntu repos - I assume you have some such repos in your sources list. 

If you want to check - comment out such in sources.list and do an update

I had similar when I installed gutsy and all was fine

---

