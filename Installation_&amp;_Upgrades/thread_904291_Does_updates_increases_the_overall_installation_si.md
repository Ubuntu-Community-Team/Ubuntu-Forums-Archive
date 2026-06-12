---
title: "Does updates increases the overall installation size ???"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by aamit_wraj on 2008-08-29
Hello everybody,
I love Ubuntu for myriad reason and also like its prompt updates...But Ive one silly question...
         **Does the regular updates increases the overall size of the freshly installed system???** Or it just patches or replaces the obsolete files and libraries???My update manager says that the update are of certain MBs depending upon the frequecy of my update cycle...Though I know that the suggested size are the download sizes but I wanted to know if it'll make changes in Installation Size proportional to it or not...I dont count over the apt-cache because I delete it continuoly after some point or backup..
Thanks in advance

---

### Post by Vivaldi Gloria on 2008-08-29
> **aamit_wraj said:**
> Or it just patches or replaces the obsolete files and libraries???

This is true in general. One exception that I know of is the kernels. When a new kernel is installed, the old ones are not deleted in case you need a fallback. If you want then you can uninstall the old kernels yourself.

---

### Post by kellemes on 2008-08-29
Maybe interesting..
[Springcleaning your apt-based distro.]("http://www.freesoftwaremagazine.com/columns/how_to_spring_clean_an_apt_based_distro")

---

### Post by kpkeerthi on 2008-08-29
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

