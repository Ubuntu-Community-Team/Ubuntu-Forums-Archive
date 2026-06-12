---
title: "deleted sources.list"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by shri_nath on 2006-06-20
Hi there,
I just installed the Ubuntu 6.06 Desktop (for an amd64 architrecture). The system also did an automatic update once using the original sources.list file.

Inadvertently I have deleted the file. Is there any way to get a copy of it ?
Or do I have to re-install the whole OS again ? It would be nice if I could just get a copy of the sources.list file (for the DapperDrake 6.60 amd64).
Thank you.

shrinath

---

### Post by aysiu on 2006-06-20
Just paste these commands into the terminal: ```
wget -c http://www.psychocats.net/ubuntu/sources.list
sudo chown root:root sources.list
sudo cp sources.list /etc/apt/sources.list
sudo aptitude update
```

---

### Post by ranf on 2006-06-21
There also is an example:
/usr/share/ubuntu-docs/ubuntu/serverguide/sample/sources.list

---

### Post by menaar on 2006-06-21
Or you can try this link.
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

---

