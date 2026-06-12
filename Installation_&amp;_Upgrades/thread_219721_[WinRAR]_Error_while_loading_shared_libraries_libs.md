---
title: "[WinRAR] Error while loading shared libraries: libstdc++.so.6"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by egomednog on 2006-07-20
When rar'ing I recieve the error: rar: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

Anyone know how to fix?

---

### Post by JerMe on 2006-07-20
installing libstdc++6 should fix it...
```
sudo apt-get install libstdc++6
```

---

### Post by egomednog on 2006-07-20
This dosen't work :( I am doing this on my server just so you know.

---

### Post by JerMe on 2006-07-20
Does /usr/lib/libstdc++.so.5 exist on your system?  If it does, maybe you can symlink libstdc++.so.6 to libstdc++.so.5 and see if that works.

---

