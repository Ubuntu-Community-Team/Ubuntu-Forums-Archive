---
title: "phpmyadmin update"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by josef.sabl on 2008-02-07
Hello, I need to upgrade my phpmyadmin (I have 2.10 and need 2.11)

The update is still not in the Ubuntu repositories but since it is only a PHP application I thought it would be okay to replace the old application files with the new ones. Maybe put them side by side and keep the same config file.

Would that work?

I was also unable to locate phpmyadmin files. Where are they in the filesystem.

Thank you.

---

### Post by bwtranch on 2008-02-07
It might work, but that's risky. Newer versions of a program may need updated dependency files , like maybe a newer version of a lib file. It is best to remove the file and then install the new one with the required dependencies. Consult the program developer for details on the specific app. this is just a rule of thumb.

---

