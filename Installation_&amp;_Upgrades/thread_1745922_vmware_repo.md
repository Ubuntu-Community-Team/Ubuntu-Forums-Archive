---
title: "vmware repo"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Vinger on 2011-05-01
Hello,

I was using virtualbox in previous versions.
Now i want to try vmware under linux after using it at work (windows)

Does anyone know is there are any repo for installing vmware (player)?

Allready thanks.

---

### Post by Vinger on 2011-05-04
No one an idea?

tx.

---

### Post by nariub on 2011-05-05
Go to vmware.com
register (free)
download the 32bit or 64bit linux version of vmplayer
 
it is a shell script.
when it is downloaded,
from a terminal run
#sh <filename>.sh
 
it's easy, and it has it's own application update facility
it does not have a deb distribution, nor is it in the software repo's

---

### Post by Vinger on 2011-05-05
Tx for the reply...
I'll do like you propose.

grz.

---

### Post by Vinger on 2011-05-07
Hello,

I tried this, but i downloaded not a shell script, but a bundle (binary)
How can i install this?
> koenh@koenh-Kubuntu:~/Downloads$ sudo sh VMware-Player-3.1.4-385536.x86_64.bundle
[sudo] password for koenh: 
VMware-Player-3.1.4-385536.x86_64.bundle: 110: Syntax error: newline unexpected
koenh@koenh-Kubuntu:~/Downloads$

tx.

---

### Post by Vinger on 2011-05-08
i installed vmware (older version) because the last version has an error.
When i open it, it has to install some extra.
> Unable to build kernel module.
See log file /tmp/vmware-root/setup-4955.log for details.
The logfile:
>  May 08 09:08:54.036: app-140495920854816| Log for VMware Workstation pid=4955 version=7.1.3 build=build-324285 option=Release
May 08 09:08:54.036: app-140495920854816| The process is 64-bit.
May 08 09:08:54.036: app-140495920854816| Host codepage=UTF-8 encoding=UTF-8
May 08 09:08:54.036: app-140495920854816| Logging to /tmp/vmware-root/setup-4955.log
May 08 09:08:54.181: app-140495920854816| modconf query interface initialized
May 08 09:08:54.181: app-140495920854816| modconf library initialized
May 08 09:08:54.218: app-140495920854816| Your GCC version: 4.5
May 08 09:08:54.228: app-140495920854816| Your GCC version: 4.5
May 08 09:08:54.244: app-140495920854816| Your GCC version: 4.5
May 08 09:08:54.265: app-140495920854816| Your GCC version: 4.5
May 08 09:08:54.280: app-140495920854816| Your GCC version: 4.5
May 08 09:08:54.328: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.331: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.334: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.337: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.340: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.362: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.365: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.368: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.371: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.374: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.381: app-140495920854816| Your GCC version: 4.5
May 08 09:08:54.397: app-140495920854816| Your GCC version: 4.5
May 08 09:08:54.441: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.444: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.447: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.450: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.453: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.460: app-140495920854816| Your GCC version: 4.5
May 08 09:08:54.476: app-140495920854816| Your GCC version: 4.5
May 08 09:08:54.539: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.542: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.545: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.548: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.551: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.949: app-140495920854816| Trying to find a suitable PBM set for kernel 2.6.38-8-generic.
May 08 09:08:54.950: app-140495920854816| Building module vmmon.
May 08 09:08:54.962: app-140495920854816| Extracting the sources of the vmmon module.
May 08 09:08:55.019: app-140495920854816| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.38-8-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.5.2
May 08 09:08:59.294: app-140495920854816| Failed to compile module vmmon!

Anyone an idea what goes wrong and how to solve it?
tx!
grz

---

### Post by Vinger on 2011-05-16
this is working.
The problem was the downloaded file.
I had to download manually, since the automated gave me a file that is only 1/5 in size...

grz.

---

