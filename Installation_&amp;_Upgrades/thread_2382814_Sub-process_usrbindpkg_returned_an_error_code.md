---
title: "Sub-process /usr/bin/dpkg returned an error code"
date: 2018-01-17
forum: Installation &amp; Upgrades
---

### Post by vincent727 on 2018-01-17
while running apt-get upgrade, got error:

```
Errors were encountered while processing:
 linux-image-4.13.0-26-generic
 linux-image-extra-4.13.0-26-generic
 linux-image-generic-hwe-16.04
 linux-generic-hwe-16.04
 linux-signed-image-4.13.0-26-generic
 linux-signed-image-generic-hwe-16.04
 linux-signed-generic-hwe-16.04
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Impavidus on 2018-01-17
Can you show the complete output of that command? A bit higher up there should be some details on that error. It's best to know the root cause of the problem.

---

### Post by vincent727 on 2018-01-17
> **Impavidus said:**
> Can you show the complete output of that command? A bit higher up there should be some details on that error. It's best to know the root cause of the problem.


Thanks for your help...
After several tries I found this problem no longer exists... I even don't know how this was resolved....:confused:

I guess one effective way was running  the code 
```

sudo apt autoremove

```

---

