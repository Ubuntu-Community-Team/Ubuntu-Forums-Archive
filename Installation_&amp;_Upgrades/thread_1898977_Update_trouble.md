---
title: "Update trouble"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by Dustin Bess on 2011-12-22
Can anyone help mewith this problem what does it mean?

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by Dustin Bess on 2011-12-22
ok sorry guys i figured it out  

sudo rm /var/lib/apt/lists/* -vf

Right?

---

### Post by Rubi1200 on 2011-12-23
> **Dustin Bess said:**
> ok sorry guys i figured it out  

sudo rm /var/lib/apt/lists/* -vf

Right?
Followed by 
```
sudo apt-get update
```

should fix the problem.

If yes, please mark this Solved using the Thread Tools near the top of the page.

---

