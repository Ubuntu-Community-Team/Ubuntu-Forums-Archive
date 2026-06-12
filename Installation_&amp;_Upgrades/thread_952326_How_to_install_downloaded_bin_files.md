---
title: "How to install downloaded bin files?"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by SheikhAmanAlam on 2008-10-19
Hi.
ive downloaded JRE 6 and JDK 6 both as a bin file, now i want to install them so that i can start java programming on ubuntu.

how to use these files for installation?

---

### Post by Elfy on 2008-10-19
Change directory to wher the file has downloaded, then make it executable

```
chmod a+x filename.bin
```

To run the file

```
./ filename.bin
``` although it might need root rights - in that case ```
sudo ./filename.bin
```

---

