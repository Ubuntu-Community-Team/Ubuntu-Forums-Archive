---
title: "unable to open files list file for package..."
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by bobpaul on 2006-09-02
Whenever I try to add or remove a packing using aptitude or synaptic I get the following error:

```
E: /var/cache/apt/archives/libgcj7-jar_4.1.0-1ubuntu8_all.deb: unable to open files list file for package `libgcj7-jar'
```

I tried re-installing libgcj7-jar but I got the same error. I also tried clearing my /var/cache/apt/archives folder, but that didn't seem to help.

---

### Post by bobpaul on 2006-09-03
Ok, I figured out what's going on I think.
```
sudo nano /var/lib/dpkg/info/libgcj7-jar.list
``` shows "new file" and gives me a blank edit window as if the file didn't exist.

```
ls -l /var/lib/dpkg/info/ | grep libgcj7-jar.list
?--------- ? ?    ?         ?      ? /var/lib/dpkg/info/libgcj7-jar.list

```

so libgcj7-jar.list is definately corrupt. Can someone send me their copy so I can recreate this file?

---

### Post by Patrick Steininger on 2006-09-12
I had the same problem, so I removed (rm) the corrupted file(s) and reinstall the package(s) with 
apt-get install --reinstall <packagename>
After that, I could install new packages without getting this error.

---

