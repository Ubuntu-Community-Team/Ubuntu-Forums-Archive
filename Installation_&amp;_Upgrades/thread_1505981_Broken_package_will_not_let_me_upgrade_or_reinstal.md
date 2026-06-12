---
title: "Broken package will not let me upgrade or reinstall"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2010-06-09
Lucid 10.04 fresh install. I had similar issues on an earlier 10.04 install and decided to wait a week or two and reinstall. Same problems.
See attached screen shot.

System shows a broken package but it will not let me upgrade. If I try to uninstall it will take too many other system files with it.

Results of:```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgp11-0
The following packages will be upgraded:
  libgp11-0
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/62.7kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file '/var/lib/dpkg/status' near line 13807 package 'libgp11-0':
 `Depends' field, invalid package name `li`c6': character ``' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
```Any solutions?

---

### Post by Rob@ThePCWiz.info on 2010-06-09
I had the same problem the last few days with 9.04, 9.10, and 10.04 (right after install).
I thought it was just the system, also, the first time isntalling 10.04 worked, and now i'm unable to reinstall 10.04 and don't know why.



**Edit:**
I haven't tried this on any other versions.

---

### Post by 73ckn797 on 2010-06-24
Re-install was the fix. Possibly could have deleted the file that had the issue but I was not sure if it would have regenerated or cause further issues.

---

