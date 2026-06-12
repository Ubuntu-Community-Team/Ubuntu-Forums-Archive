---
title: "error on trying apply updates on new hardy install"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by hcaleman on 2008-08-05
Finally installed hardy on my Portege 2000 via PXE (easy), when I sudo apt-get update I get the following error at the end of the string of code:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


Re running apt-get update shows the same issue over and over again.  Any ideas what I should do next.  This is my first linux install.

---

### Post by dileepm on 2008-08-06
Try apt-get update -f. The -f option is to fix up any dependencies or errors at the time of installing...

---

### Post by zvacet on 2008-08-06
```
sudo apt-get update && sudo apt-get upgrade
```

---

