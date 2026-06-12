---
title: "Silly question... How do I install cedega?"
date: 2005-05-24
forum: Installation &amp; Upgrades
---

### Post by GAW-Snow on 2005-05-24
I've signed up.  I've paid.  I've clicked on the link to download... How do I install the damn thing?

---

### Post by f.prisson on 2005-05-24
In which format does the file come (tar, tar.bz, tar.gz, bin, rpm...). I'm also sure you'll find some installation instruction on the cedega homepage.

---

### Post by GAW-Snow on 2005-05-24
All of the above.

Not for Ubuntu.

Remember that I am new to Linux.

---

### Post by f.prisson on 2005-05-24
for bin files:```
chmod a+x file.bin
sudo ./file.bin
``` for tar.bz files:```
tar -xvjf file.tar.bz
``` Have a look in the new created directory. For tar.gz files replace the parameter j with z. The easiest way would be to download a rpm and install it with:```
sudo alien file.rpm
sudo dpkg -i file.deb
```

---

