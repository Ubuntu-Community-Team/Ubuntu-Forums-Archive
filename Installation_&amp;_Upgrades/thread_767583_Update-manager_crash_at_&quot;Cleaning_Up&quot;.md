---
title: "Update-manager crash at &quot;Cleaning Up&quot;"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by ddcc on 2008-04-25
While updating from Gutsy to Hardy, the update-manager crashed right before "Cleaning up...", though after rebooting the system seems to be upgraded to Hardy and working ok. I would like to know is there any way to manually do the clean up though?

---

### Post by Partyboi2 on 2008-04-25
try
```
 sudo apt-get clean
```

---

### Post by ddcc on 2008-04-25
I've managed to "fix" it by using sudo apt-get clean, as well as by modifying the python source code (in a local directory) to jump straight to the cleanup function.

---

