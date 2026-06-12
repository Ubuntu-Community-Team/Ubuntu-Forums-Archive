---
title: "[SOLVED] Uninstalling Avast"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by KeybladeSephi on 2008-06-27
Hello, everyone. I was wondering how do you completely uninstall Avast? I don't exactly need it, but haven't found a way to remove it completely. Could someone please help me? Thank you =]

---

### Post by Partyboi2 on 2008-06-29
If you installed it as a deb try
```
sudo apt-get remove --purge  avast4workstation
```

Edit: You may need to replace avast4workstation with the correct name. You can look for the correct package name by
```
 dpkg -l | less
```

---

### Post by KeybladeSephi on 2008-06-29
Thank you so much, Partyboi2! =D

---

