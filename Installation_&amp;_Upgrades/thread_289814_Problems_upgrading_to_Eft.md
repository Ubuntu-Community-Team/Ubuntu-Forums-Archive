---
title: "Problems upgrading to Eft"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by th3gh05t on 2006-10-31
Hi,

I ran the gksu "update-manager -c" command, and everything seemed to working fine, but it failed when it came to downloading the files.

I tried to copy the error, but it wouldn't let me copy and paste the error window that came up.

Is there something wrong with my sources.list file? Should I sue this [one]("http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2")?


Thanks for your time!

th3gh05t

---

### Post by John.Michael.Kane on 2006-10-31
Try this

```
sudo gedit /etc/apt/sources.list
```
replace all occurrences of the word dapper with the word edgy

Then run:
```
sudo aptitude update 
```
followed by:
```
sudo aptitude dist-upgrade
```

---

