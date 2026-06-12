---
title: "Nvidia error - Invalid cross-device link"
date: 2024-04-06
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2024-04-06
Just did a update using Ubuntu 22.04LTS and I getting 3 error messages constantly, with the same ending as in the Title. First stupid question - do I need to update NVIDIA every time I get a notification, even though my hardware remains the same. If that's a yes, then that's the answer.

---

### Post by #&amp;thj^% on 2024-04-06
If nVidia is installed through ubuntu sources all should be good, and this is commonly a cuda error.

My question is how did you install nvidia?
Maybe show us this:
```
sudo apt --fix-broken install
```

Post that back here so we can see more details please

---

### Post by Alligator on 2024-04-06
I checked the installed drivers and did an autoinstall.  Everything was good.  Then a did a reboot and that fixed it.  Thanks for responding.

---

### Post by #&amp;thj^% on 2024-04-06
Good to hear.

---

