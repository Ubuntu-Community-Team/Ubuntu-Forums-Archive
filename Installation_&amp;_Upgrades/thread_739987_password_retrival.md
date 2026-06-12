---
title: "password retrival"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by anith on 2008-03-30
i forgot my password for login to ubuntu... what i should do to retrive my password...:(

---

### Post by bapoumba on 2008-03-30
From grub menu, boot in recovery mode. You'll be root with a # prompt (no GUI).
```
# passwd <your_login>
```
where <your_login> is your current user login, do not write the <>. You'll be able to set up  new one.
Then:
```
# reboot
```

---

