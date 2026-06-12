---
title: "The following packages are BROKEN:"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by HilliBilly on 2007-02-08
hi,

do not really understand what this question means. should i accept this solution to resolve the dependencies or should i let everything as it is?

(edgy, gnome, uname -r shows: 2.6.17-10-386)

**aptitude -s --show-deps dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-image-386 (D: linux-image-2.6.17-11-386) 
  linux-restricted-modules-2.6.17-11-386 (D: linux-image-2.6.17-11-386) 
The following packages will be upgraded:
  linux-restricted-modules-386 
2 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7934kB of archives. After unpacking 21.4MB will be used.
The following packages have unmet dependencies:
  linux-image-386: Depends: linux-image-2.6.17-11-386 which is a virtual package.
  linux-restricted-modules-2.6.17-11-386: Depends: linux-image-2.6.17-11-386 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-386
linux-restricted-modules-386

Keep the following packages at their current version:
linux-image-386 [2.6.17.10 (edgy, now)]
linux-restricted-modules-2.6.17-11-386 [Not Installed]

Score is -693

Accept this solution? [Y/n/q/?] 


**sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

[B]
aptitude search ~Dlinux.*386 | sort | uniq[/B]
i   linux-386                       - Complete Linux kernel on 386.             
i   linux-image-386                 - Linux kernel image on 386.                
i   linux-restricted-modules-2.6.15 - Non-free Linux 2.6.15 modules on 386      
i   linux-restricted-modules-2.6.17 - Non-free Linux 2.6.17 modules on 386      
i   linux-restricted-modules-386    - Restricted Linux modules on 386.          
p   kernel-image-netbootable        - net-bootable kernel for use with diskless 
p   linux-headers-386               - Linux kernel headers on 386               
p   linux-restricted-modules-2.6.17 - Non-free Linux 2.6.17 modules on 386

---

### Post by kalahari875 on 2007-02-08
Having the same problem.

The following packages have been kept back:
  linux-headers-386 linux-headers-generic linux-image-generic

apt-get dist-upgrade will not install them either.

---

### Post by banditti on 2007-02-08
it is a new club

[http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)

---

### Post by tungv0 on 2007-02-08
I have the same problem as well, when I update ubuntu, those 3 packages has been left

---

