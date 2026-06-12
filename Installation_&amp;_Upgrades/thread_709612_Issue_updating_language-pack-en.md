---
title: "Issue updating language-pack-en"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by riverfr0zen on 2008-02-27
I just tried to update my laptop (Gutsy) and received the error below. Does anyone have any ideas on how to resolve this?

The following packages will be upgraded:
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6644kB of archives.
After unpacking 4096kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/language-pack-en_1%3a7.10+20080205_all.deb (--unpack):
 unable to open files list file for package `wpasupplicant': Permission denied
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-en_1%3a7.10+20080205_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zvacet on 2008-02-27
```
sudo dpkg --configure -a
```

or

```
sudo apt-get -f install
```

---

