---
title: "Problem in Ubuntu9.10 i need help"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by killjoy27 on 2010-02-16
i cant seem to really do much because every time i do something it said permissions denied...i installed ihe OEM manfuactures option when i booted from CD.now i cant get the main admin account.

---

### Post by ajgreeny on 2010-02-16
I suspect that when you made the new user, ie you in your username, you did not add yourself to the admin group.  I have never seen an oem install of ubuntu, so have no idea what would normally be needed to add the first admin user, but I'm sure you should be able to add yourself to the admin group by booting to recovery mode and then using the command ```
adduser username admin
```changing username to what you chose when you made your new user, of course.

---

