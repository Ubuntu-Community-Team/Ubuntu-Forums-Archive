---
title: "Cannot Install Any Packages/Updates"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by Locutus_of_Borg on 2007-11-10
> none@blank:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  cupsys cupsys-bsd cupsys-client cupsys-common libcupsimage2 libcupsys2
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2945kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libcupsys2_1.2.8-0ubuntu8.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `openoffice.org-common': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libcupsys2_1.2.8-0ubuntu8.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
none@blank:~$ cat /etc/issue
Ubuntu 7.04 \n \l

none@blank:~$ uname -r
2.6.20-16-generic
none@blank:~$ exit    

I get the same thing when using package manager to install any .deb files as well, only where it says "/var/cache/apt/archives/libcupsys2_1.2.8-0ubuntu8.1_i386.deb" it lists the .deb I'm trying to install.

Please help.

Thank you.

---

### Post by Locutus_of_Borg on 2007-11-11
Sunday Bump.

---

### Post by Locutus_of_Borg on 2007-11-14
err, wednesday repeat bump?

---

### Post by Locutus_of_Borg on 2007-11-19
hopeless, doesn't want to re-install bump

---

### Post by Locutus_of_Borg on 2007-11-29
I ran e2fsck -cc -C stdout /dev/sda2 from a live cd again, it fixed some errors, then i copied the file I was getting the buffer_read error with into my /var/lib/dpkg/info directory and now it seems to be working, for anyone who might get this same problem.

---

