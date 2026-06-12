---
title: "Cant update."
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by mdmytryk on 2008-10-01
For some reason i cant get any updates.  I get an error that says there was a problem while checking for updates.  When i go to System>administration>update manager, it closes automatically.  I tried updating via terminal, sudo apt-get install update, no luck. It says Segmentation faulty tree... 0%
then nothing.  

Any ideas?

---

### Post by overdrank on 2008-10-01
> **mdmytryk said:**
> For some reason i cant get any updates.  I get an error that says there was a problem while checking for updates.  When i go to System>administration>update manager, it closes automatically.  I tried updating via terminal, sudo apt-get install update, no luck. It says Segmentation faulty tree... 0%
then nothing.  

Any ideas?

Hi and the command would be
```
sudo apt-get update
```
And can you post the exact error.
If that command works then you can replace update with upgrade.

---

### Post by mdmytryk on 2008-10-01
O. Thank you.

---

