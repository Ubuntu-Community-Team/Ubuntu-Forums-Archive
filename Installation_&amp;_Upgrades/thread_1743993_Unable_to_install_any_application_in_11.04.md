---
title: "Unable to install any application in 11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by pavankumar25386 on 2011-04-30
Unable to install any application... I have tried to install 'Startup manager' it is giving following error:

[B]pavan@pavan:~$ sudo apt-get install startupmanager menu
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_natty_free_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.[/B]

When i tired to open Symantic Package manager following error displayed:

[B]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_natty_free_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/B]


Please help regarding this...

---

### Post by cariboo on 2011-04-30
Remove:

>  /var/lib/apt/lists/packages.medibuntu.org_dists_natty_free_binary-amd64_Packages

and try again.

---

### Post by pavankumar25386 on 2011-04-30
p**avan@pavan:~$ sudo rm /var/lib/apt/lists/packages.medibuntu.org_dists_natty_free_binary-amd64_Packages **

I have removed and tried again, i see problem is not fixed

[I]pavan@pavan:~$ sudo apt-get install startupmanager menu
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_natty_non-free_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.[/I]

---

### Post by pavankumar25386 on 2011-04-30
I fixed mine by doing:

Code:

sudo rm /var/lib/apt/lists/*

Thnx for the suport

---

