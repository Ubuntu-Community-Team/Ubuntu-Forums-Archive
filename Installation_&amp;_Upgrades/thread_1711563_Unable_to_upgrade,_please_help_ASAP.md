---
title: "Unable to upgrade, please help ASAP"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by robinsh123 on 2011-03-21
I am getting the error message as shown in attached image 
what is really a screenshot.

---

### Post by sikander3786 on 2011-03-22
Click the 'Check' button in Update Manager to refresh your repository index or go to Terminal and run this command.

```
sudo apt-get update
```

If the error persist even after, go to Software Center > Edit > Software Sources and choose 'Main' server for your download. Close and click 'Reload' in the pop up window. The error should go away then...

---

