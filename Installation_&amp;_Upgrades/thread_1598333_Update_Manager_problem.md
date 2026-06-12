---
title: "Update Manager problem"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2010-10-16
Running Ubuntu 10.10 32 bit.
Update Manager lists an Important Security Update for "Header files related to Linux kernel version 2.6.35." (see attached screen shot). The update will not install and returns the following error: 
```
Preparing to replace linux-headers-2.6.35-22 2.6.35-22.33 (using .../linux-headers-2.6.35-22_2.6.35-22.34_all.deb) ... 
Unpacking replacement linux-headers-2.6.35-22 ... 
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.35-22_2.6.35-22.34_all.deb (--unpack): 
 corrupted filesystem tarfile - corrupted package archive 
No apport report written because MaxReports is reached already
dpkg-deb: subprocess paste killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-headers-2.6.35-22_2.6.35-22.34_all.deb
``` I am thinking that I only need to delete the downloaded package and re-run the update manager. Any suggestions?

EDIT: Deleted package and ran Update Manager and package installed properly.

---

### Post by Rocket2DMn on 2010-10-16
Sounds like the downloadd file is corrupt. Try cleaning out your apt cache and re-downloading the updates:
```
sudo apt-get clean
```
Then try your updates again.

---

### Post by 73ckn797 on 2010-10-16
> **Rocket2DMn said:**
> Sounds like the downloadd file is corrupt. Try cleaning out your apt cache and re-downloading the updates:
```
sudo apt-get clean
```Then try your updates again.

I posted the thread but immediately went in and deleted the particular package which corrected the problem. Your tip was what I was doing, probably while you were replying. Thanks for the input anyway.

---

