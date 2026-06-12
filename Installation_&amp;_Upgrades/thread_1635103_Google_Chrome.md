---
title: "Google Chrome"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by elsneakums on 2010-12-01
I installed Google Chrome from a deb in 10.04 and it seems to work however when i click the package manager i get this error:

E: Malformed 3rd word in the Status line
E: Error occurred while processing libavahi-common-data (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

How do i go about uninstalling Google Chrome?

---

### Post by v1ad on 2010-12-01
sudo apt-get --purge remove google-chrome-stable 

and then reinstall.... or it should be in your package manager. look in installed programs..

---

### Post by elsneakums on 2010-12-01
Tried that command in the terminal and get this:

sudo apt-get --purge remove google-chrome-stable
Reading package lists... Error!
E: Malformed 3rd word in the Status line
E: Error occurred while processing libavahi-common-data (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

My software centre also says ive got 0 items installed!

---

### Post by v1ad on 2010-12-01
hmm seems like your package list is screwed up.. do 
sudo apt-get update 

twice, then sudo apt-get upgrade -y

if chrome doesn't work then, try removing it again and reinstallling

---

### Post by sikander3786 on 2010-12-01
Edit your status file by,

```
gksudo gedit /var/lib/dpkg/status
```

Search for libavahi-common-data. Its status line should read like this

> Status: install ok installed

There is something malformed there. Correct it, save and close and try again.

---

### Post by elsneakums on 2010-12-01
Just keep getting the same error message over and over. Any other ideas?

---

### Post by sikander3786 on 2010-12-01
> **elsneakums said:**
> Just keep getting the same error message over and over. Any other ideas?
Did you try the advice in my above post?

---

### Post by elsneakums on 2010-12-02
Yeah i got a big red button with a white line through it come up, in the end i reinstalled 10.04
Thanks for the help

---

