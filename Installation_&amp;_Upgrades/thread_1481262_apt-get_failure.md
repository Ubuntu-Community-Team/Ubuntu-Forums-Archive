---
title: "apt-get failure"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by bl00dang3l on 2010-05-12
As trying to update my system the other day I was greeted with a message I did not want.

```
tpsv@titantest:~$ sudo apt-get install update
Reading package lists... Error!
E: Problem parsing dependency Replaces
E: Error occurred while processing language-pack-kde-nds (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```Any help would be great! Thanks

---

### Post by Soul-Sing on 2010-05-12
```
sudo rm -f /var/lib/dpkg/lock
```

```
sudo apt-get update
```

or
```

sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

### Post by bl00dang3l on 2010-05-12
> **leoquant said:**
> ```
sudo rm -f /var/lib/dpkg/lock
```

```
sudo apt-get update
```

or
```

sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```
Thanks the second option worked. Can you explain to me why?

---

### Post by Soul-Sing on 2010-05-13
It is a hard "reset" and new build-up of your -apt-lists, the rebuild is done via apt-get update.
normally a partial rm (language-pack-kde-nds) is enough, but for some reason a partial removal doesn't work very often.

---

