---
title: "Update manage and Software center not workin"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by Konoha on 2010-12-22
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

(used the terminal to update it)

The above is the mesage i get when i try to update my Ubuntu 10.10. i installed it from scratch ever since i did so the software center does not work and the update manger from the systems>administrations menu also does not work.

32 bit systestem.

SOS

---

### Post by JBAlaska on 2010-12-22
Please post results of ```
ls /var/lib/dpkg/status*
```

---

### Post by karthick87 on 2010-12-22
Try,
```
sudo apt-get clean
```
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```

---

### Post by sikander3786 on 2010-12-22
Try using an older dpkg/status file.

Applications > Accessories > Terminal:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get update && sudo apt-get upgrade
```

If that doesn't work, post the output of commands that other members have asked for above.

---

