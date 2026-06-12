---
title: "Want to upgrade to 18.04.3 from 18.04.1"
date: 2019-10-03
forum: Installation &amp; Upgrades
---

### Post by rpwood on 2019-10-03
I running Ubuntu 18.04.1 on a dual boot machine with Win10. My 18.04.1 seems to be working fine EXCEPT I want to upgrade to 18.04.3. How do I do that? Sorry still a newbie.

Thanks in Advance.

---

### Post by Skaperen on 2019-10-03
boot into Ubuntu 18.04.1 and been sure your internet connection is started and working.  then do these 2 commands:
```

sudo apt-get update
sudo apt-get -y dist-upgrade

```
this can take several minutes, depending on your internet speed.

---

### Post by rpwood on 2019-10-03
Thank you. I remembered to use Software Updater.

---

### Post by ubfan1 on 2019-10-03
The previous upgrades everything except the kernel 4.15.
For the 9 month support kernel, (5.0 ?) upgrade which 18.04.3 uses, add:
sudo apt-get install --install-recommends linux-generic-hwe-18.04 xserver-xorg-hwe-18.04

---

