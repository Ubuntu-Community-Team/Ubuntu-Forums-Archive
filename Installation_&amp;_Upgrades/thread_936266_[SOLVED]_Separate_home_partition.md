---
title: "[SOLVED] Separate /home partition"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by GhentK on 2008-10-02
Just a simple yes/no question.

I have Ubuntu installed to /dev/sda6 and a separate /home partition on /dev/sda7. If I reinstall Ubuntu to /dev/sda6 and set /dev/sda7 as my /home, will any data on /dev/sda7 be affected during the installation?

---

### Post by Pumalite on 2008-10-02
Go Manual; choose /dev/sda7 as /home, but DO NO FORMAT

---

### Post by y@w on 2008-10-02
In fact, if I recall correctly, the installer will detect that there are old users on that filesystem and prompt you to set that user up again.

---

### Post by haydnc on 2008-10-02
The one word answer to your question is "No"...

Unless you forget and format /dev/sda7 whilst doing the install of Ubuntu on /dev/sda6.

During the install when you get to the partitioning section select manual partitioning and set /dev/sda7 as /home, do not chose to format the partition and everything will be fine.

---

### Post by GhentK on 2008-10-02
> **Pumalite said:**
> Go Manual; choose /dev/sda7 as /home, but DO NO FORMATI thought as much; I just needed confirmation. :)

> **y@w said:**
> In fact, if I recall correctly, the installer will detect that there are old users on that filesystem and prompt you to set that user up again.Convenient. :D

Thanks all. :D

---

