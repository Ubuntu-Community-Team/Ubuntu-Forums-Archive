---
title: "Linux Kernel 3.20.-38"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by marech on 2013-03-05
Unter Ubuntu 12.04 64bit scheitert auf meinem Rechner die Installation des Pakets "Linux kernel image for version 3.2.0 on 64bit x86 SMP" (linux-image-3.2.0-38-generic)

Folgende Fehlermeldung erscheint:

[FONT=verdana][I]installArchives() failed: Setting up linux-image-3.2.0-24-generic (3.2.0-24.39) ... 
Running depmod. 
sh: 1: /usr/sbin/update-initramfs: not found 
Failed to create initrd image. 
dpkg: error processing linux-image-3.2.0-24-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-38-generic (3.2.0-38.60) ... 
Running depmod. 
sh: 1: /usr/sbin/update-initramfs: not found 
Failed to create initrd image. 
dpkg: error processing linux-image-3.2.0-38-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-3.2.0-38-generic; however: 
  Package linux-image-3.2.0-38-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic:No apport report written because the error message indicates its a followup error from a previous failure.
 
 linux-generic depends on linux-image-generic (= 3.2.0.38.46); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 linux-image-3.2.0-24-generic 
 linux-image-3.2.0-38-generic 
 linux-image-generic 
 linux-generic 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
Setting up linux-image-3.2.0-24-generic (3.2.0-24.39) ... 
Running depmod. 
sh: 1: /usr/sbin/update-initramfs: not found 
Failed to create initrd image. 
dpkg: error processing linux-image-3.2.0-24-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-38-generic (3.2.0-38.60) ... 
Running depmod. 
sh: 1: /usr/sbin/update-initramfs: not found 
Failed to create initrd image. 
dpkg: error processing linux-image-3.2.0-38-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-3.2.0-38-generic; however: 
  Package linux-image-3.2.0-38-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 3.2.0.38.46); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured [/I][/FONT]

Hat jmd einen Tipp, wie dies zu lösen sein könnte?

---

### Post by sanderj on 2013-03-05
Tip 1: In this forum speak English, not German.
Tip 2: "/usr/sbin/update-initramfs: not found " solve that .... install "initramfs-tools". Then try again.

---

### Post by marech on 2013-03-19
Thank you very much. I am not able to install the initramfs-tool is there an other opportunity to solve my problem?

---

### Post by sanderj on 2013-03-19
> **marech said:**
> Thank you very much. I am not able to install the initramfs-tool is there an other opportunity to solve my problem?

Post the output of



```
sudo apt-get install initramfs-tools
```

(And don't make typing mistakes)

---

