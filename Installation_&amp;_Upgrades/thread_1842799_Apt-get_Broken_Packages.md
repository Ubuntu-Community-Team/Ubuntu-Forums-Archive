---
title: "Apt-get Broken Packages"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by r_anjit on 2011-09-12
when I try to install wine through Apt-get I get the following message

libc6-dev: Breaks: gcc-4.4 (< 4.4.6-4) but 4.4.3-4ubuntu5 is to be installed
E: Broken packages

How shall I resolve the issue.

Please help !!
Thanks .

---

### Post by An Sanct on 2011-09-12
The dialog probably says to use apt-get install -f, to repair broken packages, so do this

```
sudo apt-get install -f
```

and provide your password. If this step fails, inform us

PS. Are you using Oneiric? I have the same problem with Oneiric and am guessing, that it is just a temporary state, since it is a beta.

---

