---
title: "Initial group memberships / conferred permissions?"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by zeveck on 2007-05-22
The user created during install is in a whole bunch of groups. When I tried to create a second user using useradd the system failed to create the user's home directory (I had to do it manually), and the new user isn't in any groups. I don't want to just blindly add the new user to everything, but cannot find a reference describing the abilities conferred by each group membership. Can somebody point me at such a description?

---

### Post by zvacet on 2007-05-22
```
sudo adduser user_name
```

After that go to the users&groups select new user and go to the advanced tab.You can give all privileges to the new user exept administrator´s one.

---

