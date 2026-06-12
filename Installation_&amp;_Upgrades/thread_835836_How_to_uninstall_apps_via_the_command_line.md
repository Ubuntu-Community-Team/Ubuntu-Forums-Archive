---
title: "How to uninstall apps via the command line"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by Kain000 on 2008-06-20
HOw can I uninstall apps from the command line?

---

### Post by abn91c on 2008-06-20
sudo aptitude remove file-name

---

### Post by Kain000 on 2008-06-20
> **abn91c said:**
> sudo aptitude remove file-name

thankyou very much

---

### Post by iaculallad on 2008-06-20
For DEB packages:

```
sudo dpkg -r package_name
```

---

