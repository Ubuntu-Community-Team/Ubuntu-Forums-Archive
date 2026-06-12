---
title: "E:Read error - read (0: Success), E:Problem closing the gzip file /var/lib/apt/lists/"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by mndotmail on 2011-11-29
Kindly help me with this error.

E:Read error - read (0: Success), E:Problem closing the gzip file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Translation-en - close (0: Success), E:The package lists or status file could not be parsed or opened.

While updating my Ubuntu 11.10 i am getting this error and it says "This is a serious problem. Try again later. If this problem appears again, please report an error to the developers."

---

### Post by raja.genupula on 2011-11-29
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by mndotmail on 2011-11-30
> **raja.genupula said:**
> ```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

Thanks Raja,

That worked like charm.
This community rocks.. :P

---

### Post by raja.genupula on 2011-11-30
thats good news man , please mark the thread as solved from thread tools

Thank you .

---

