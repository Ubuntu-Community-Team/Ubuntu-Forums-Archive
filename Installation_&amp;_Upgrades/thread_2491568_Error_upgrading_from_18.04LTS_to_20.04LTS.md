---
title: "Error upgrading from 18.04LTS to 20.04LTS"
date: 2023-10-13
forum: Installation &amp; Upgrades
---

### Post by nonetheless on 2023-10-13
I had a fresh reinstall of 16.04. Then upgraded to 18.04 and then to 20.04.

While upgrading through "**Software Updater**", it faced with an error:
 Could not install the package
```
/tmp/apt-dpkg-install-JCuWPV/07-apparmor_2.13.3-7ubuntu5.2_amd64.deb package may not be in working state
```
Please consider supporting a bug report.
```
new apparmor package pre-installation script subprocess returened error exit status 1
```


And it continued. The process ended with *could not install upgrade*.
```
The upgrade has aborted. Your system could be in an unstable state. A recovery will run now(dpkg--configure-a)
```

Which returned with 
```
The upgrade is completed but there were errors during the upgrade process.
```

The system did not go through **cleaning up** and **restarting process** and everything aborted.

What is this error?  Should I remove Apparmor package or reinstall it or what? Please guide me through this.

---

