---
title: "Advise : Update ubuntu"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by deep2sunny on 2012-07-18
today i've installed ubuntu 12.04 LTS. Should I update it or leave it like that. Because last time when I had installed Ubuntu n updated it I started facing errors like "System Program Problem Detected" n internal errors. So it is recommended to update it. If yes what is the safest method to do so? Is it by Ubuntu's Update Manager or the terminal. If by terminal plz tell me the commands to do it? Advise :popcorn:

---

### Post by prshah on 2012-07-18
> **deep2sunny said:**
> today i've installed ubuntu 12.04 LTS. Should I update it or leave it like that. Because last time when I had installed Ubuntu n updated it I started facing errors like "System Program Problem Detected" n internal errors. So it is recommended to update it. If yes what is the safest method to do so? Is it by Ubuntu's Update Manager or the terminal. If by terminal plz tell me the commands to do it? Advise :popcorn:

Yes, you must update, and keep updating regularly.

The "System Problem Detected" errors are a common issue for this release, but disappear after a while (typically as updates are applied).

You can use either update-manager or the terminal to update; both are equally effective. 

Terminal command for updating:```
sudo apt-get update && sudo apt-get -y upgrade
```

---

