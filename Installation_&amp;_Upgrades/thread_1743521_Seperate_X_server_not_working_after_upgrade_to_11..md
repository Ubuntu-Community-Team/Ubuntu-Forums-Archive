---
title: "Seperate X server not working after upgrade to 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by bardu on 2011-04-29
After upgrading to 11.04 (x64) in the second monitor I see just the background but no desktop.
X server configuration was done in previous versions with NVIDIA X server settings tool.

---

### Post by bardu on 2011-04-29
No one else has this issue?

---

### Post by ataraxic on 2011-04-30
I've got the same problem...
Xserver is not started by default.
Any thoughts?

I've just notice in the startx log: (EE) NVIDIA: Failed to load the NVIDIA kernel module.

So somehow it is missing now.
If I boot with previous 10.10 -- everything working just fine.

---

### Post by Santa_Claus on 2011-04-30
Hi,
Same problem here with ati graphic card. 

I got problem solved with these instructions:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Especially: "Removing the proprietary fglrx driver was usefull"

BR
Santa_Claus

---

