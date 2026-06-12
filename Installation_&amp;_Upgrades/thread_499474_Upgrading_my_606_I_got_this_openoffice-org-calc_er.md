---
title: "Upgrading my 606 I got this openoffice-org-calc error"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by magnus07 on 2007-07-12
Preparing to replace openoffice.org-calc 2.0.2-2ubuntu12 (using .../openoffice.org-calc_2.0.2-2ubuntu12.4_i386.deb) ...
Unpacking replacement openoffice.org-calc ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org-calc_2.0.2-2ubuntu12.4_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libscui680li.so')
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-calc_2.0.2-2ubuntu12.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


Ideas? Failed twice.

---

### Post by rodrigueskevin on 2007-07-28
Hi,
I have ubuntu 7.04 installed and when i try to update ubuntu I get error that the packages are broken and to fix them using apt-get install -f

so i give the command
sudo apt-get install -f

Following is the screen with the errors:

Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python2.4-minimal python2.4 python-wxversion libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openoffice.org-common openoffice.org-core
Recommended packages:
  openoffice.org-style-industrial openoffice.org-style-tango
  openoffice.org-style-crystal openoffice.org-style-andromeda
  openoffice.org-style-hicontrast nfs-common
The following packages will be upgraded:
  openoffice.org-common openoffice.org-core
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
12 not fully installed or removed.
Need to get 0B/47.5MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? (Reading database ... 95012 files and directories currently installed.)
Preparing to replace openoffice.org-common 2.2.0-1ubuntu3 (using .../openoffice.org-common_2.2.0-1ubuntu4_all.deb) ...
Unpacking replacement openoffice.org-common ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Preparing to replace openoffice.org-core 2.2.0-1ubuntu3 (using .../openoffice.org-core_2.2.0-1ubuntu4_i386.deb) ...
Unpacking replacement openoffice.org-core ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_2.2.0-1ubuntu4_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu4_all.deb
 /var/cache/apt/archives/openoffice.org-core_2.2.0-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help as I cannot install any other software until this problem is resolved.

---

### Post by magnus07 on 2007-08-01
guss this is the wrong thread to post it
btw, i got into many problems with 7.04 on my old machine

---

### Post by Seisen on 2007-08-01
Try this magnus07

```
cd /var/cache/apt/archives/
dpkg -i --force-install openoffice.org-calc_2.0.2-2ubuntu12.4_i386.deb.deb
```

rodrigueskevin, try the same thing except substitiute which ever package is not installing.

If you both of you are still getting errors please post them after trying this.

---

### Post by rodrigueskevin on 2007-08-03
Hi,
I've not used my machine for some time now. But I think I found the solution to my problem.
I changed the location of the servers from which I got my updates. Being from India, I had initially selected a server in India but I found that those package updates for openoffice were corrupted. I just switched to another server and the updater seems fine. 
Others who have such a problem can also try.

---

