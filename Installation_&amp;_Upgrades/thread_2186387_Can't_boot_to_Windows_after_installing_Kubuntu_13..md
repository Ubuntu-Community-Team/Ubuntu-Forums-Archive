---
title: "Can't boot to Windows after installing Kubuntu 13.10"
date: 2013-11-07
forum: Installation &amp; Upgrades
---

### Post by jarrettlolhi on 2013-11-07
Hello, I recently installed Kubuntu 13.10 from a USB to an external hard drive, and I have Windows in the internal SSD. After attempting to boot from the external drive, I was presented with a "no such partition" error. So, I used [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) to fix the problem. This did allow Kubuntu to boot from the external, however, when I attempt to boot from the SSD, it boots Kubuntu instead. I can still see the Windows files and partition, but I can't actually boot to it.

---

### Post by Bucky Ball on 2013-11-07
Open a terminal and try:

```
sudo update-grub
```

That should pick Windows up. When you re-boot, hold down the shift key and that should bring up a grub menu with Win and Ubuntu to choose from.

---

### Post by fantab on 2013-11-07
Post the LINK to BootInfo-Summary that Boot-Repair generates.

---

### Post by jarrettlolhi on 2013-11-07
That worked, thanks

---

### Post by Bucky Ball on 2013-11-07
Great news! Welcome, incidentally. Please mark the thread as solved by following the instructions in my signature. Enjoy! ;)

---

