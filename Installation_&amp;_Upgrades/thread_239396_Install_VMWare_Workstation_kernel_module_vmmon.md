---
title: "Install VMWare Workstation kernel module vmmon"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by ajaustin on 2006-08-19
Sometimes it is necessary to compile the kernel module vmmon in order to get the Linux host to work.  I installed the kernel source packages - linux-headers-2.6.15-26-386 and linux-source-2.6.15 (in my case for the 2.6.15-26-386 running kernel), but still had some trouble getting vmware-config.pl to run as it could not find the header files

I solved the problem by making a symbolic link for the include directory as per the first posting in this thread: [http://www.vmware.com/community/thread.jspa?messageID=415731&#415731](http://www.vmware.com/community/thread.jspa?messageID=415731&#415731)

---

