---
title: "[SOLVED] Error with 'libflckrnet2.1.5-cil'"
date: 2008-12-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2008-12-18
Encountered this message during update this morning. 
Has any one else seen this and is it some thing I need to be concerned about?

```
dougie@DougiesLeanMachine:~$ sudo dpkg --configure -a
Setting up libflickrnet2.1.5-cil (25277-6ubuntu1) ...
* Installing 1 assembly from libflickrnet2.1.5-cil into Mono
! Assembly /usr/share/cli-common/policies.d/libflickrnet2.1.5-cil/policy.2.1.FlickrNet.dll does not exist
dpkg: error processing libflickrnet2.1.5-cil (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libflickrnet2.1.5-cil

```

---

### Post by philinux on 2008-12-18
Same here. I dont use flickr so I'm not bothered at this stage. I'm sure it will get fixed.

---

### Post by phoogkamer on 2008-12-18
Just run the update again. I had this issue as well, but after a aptitude update && aptitude safe-upgrade this issue was resolved.

Tux

---

### Post by directhex on 2008-12-18
Mono packaging bug - cli-al and cli-sn tools are not correctly symlinked, which causes dh_cligacpolicy to fail, which causes the named file to be missing when creating lib packages

---

### Post by DougieFresh4U on 2008-12-18
> **phoogkamer said:**
> Just run the update again. I had this issue as well, but after a aptitude update && aptitude safe-upgrade this issue was resolved.

Tux

'safe-upgrade' wants to remove 3 packages and I'm not to keen on letting packages get removed
```
The following packages will be REMOVED:
  libblas3gf{u} libgfortran3{u} liblapack3gf{u} 
The following packages will be upgraded:
  python-numpy 
The following partially installed packages will be configured:
  libflickrnet2.1.5-cil 
1 packages upgraded, 0 newly installed, 3 to remove and 41 not upgraded.
Need to get 2273kB of archives. After unpacking 6758kB will be freed.
Do you want to continue? [Y/n/?] n
```

---

### Post by DougieFresh4U on 2008-12-18
Update seems to have resolved issue. Package has instaqlled no errors.

---

