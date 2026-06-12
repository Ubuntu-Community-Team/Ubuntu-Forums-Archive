---
title: "grub2 detection of other os"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by kathmary on 2010-05-02
I was wondering how to prevent grub2 from detecting operating systems on other hard drives.  I have Ubuntu Lucid on the second hard drive with windows 7 on the primary (unplugged for now).

---

### Post by frantid on 2010-05-02
If you really don't want it to find others, take away the execute bit from /etc/grub.d/30_os-prober

```
sudo chmod 644 /etc/grub.d/30_os-prober
```

---

### Post by kathmary on 2010-05-02
Thank you very much!  I googled and searched the forums but could not find this info.  Appreciate your answer!

---

