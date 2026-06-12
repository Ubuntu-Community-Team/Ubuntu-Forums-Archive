---
title: "grub-pc upgrade error"
date: 2020-01-24
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2020-01-24
This afternoon I updated 2 similar computers with 18.04 LTS. One went just fine. However I got an error upgrading grub-pc on the second one.

```
Setting up grub-pc (2.02-2ubuntu8.14) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
```

I've tried the usual fixes:

```
dpkg --configure -a
apt install -f
apt install --reinstall
apt autoclean

```

All return the same error. I've googled the the error and none of the posts seem current.
I can remove the package but any attempt to reinstall it generates the same error.
```
apt remove pc-grub
```


Oddly looking at the logs for the first computer I updated it seems to have updated grub-pc correctly.

---

### Post by oldfred on 2020-01-24
There is this bug, but not sure if real bug or not:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1848826](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1848826)

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

What brand/model system?
What video card/chip?

Update or new install?
If update, did you remove all proprietary drivers & ppas?

---

### Post by rsteinmetz70112 on 2020-01-26
This was a typical

```
apt update
apt full-upgrade.
```

The computer had been upgraded from 16.04 more than a year ago. It's been running fine since then.
I found some references to older bugs that had the same a error message, but I missed the Launchpad bug but you found.

Oddly another computer set up very similarly upgraded grub-pc just fine.

I'm away from the site until Wednesday so I'll check everything again then.

---

### Post by rsteinmetz70112 on 2020-01-26
I have subsequently update four other similar computers running 18.04 at another site with no error.
A straightforward bug seems unlikely.

---

### Post by rsteinmetz70112 on 2020-02-02
I have returned after a week out of town. Ok This is a little odd. I updated all of my computers at the original site and all ran perfectly. The error went away. 
I'm going to make this one solved.

---

### Post by rsteinmetz70112 on 2020-02-20
OK this same error just showed up on another machine. Similar hardware to the others.

---

