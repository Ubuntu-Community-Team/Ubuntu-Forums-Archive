---
title: "Hash Sum mismatch when upgrading from 16 LTS to 18 LTS"
date: 2018-08-19
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2018-08-19
I'm getting the attached error when upgrading from 16 LTS to 18 LTS. Have changed repositories, but issue remains.

---

### Post by oldos2er on 2018-08-19
Try ```
sudo rm -rf /var/lib/apt/lists/*

sudo apt update
```

---

### Post by lister171254 on 2018-08-19
Thanks,
That did the job

---

