---
title: "Copying file in /usr/src"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by Sikandar on 2010-02-18
I need to copy certain folder in /usr/src/linux-heasders/drivers/staging directory.
**Attempts made are:**
1.cp command:
 with and without -t option.
 output:> file omitted
2chmod a+wx directory name
 > output: Permission denied.
3.sudo cp source destination
 > output:file omitted.

---

### Post by Sikandar on 2010-02-19
Done copying.
Solution:
**sudo chmod a+w folder name**

---

