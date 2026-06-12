---
title: "Error on Upgrade failed in buffer_read(fd)"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by martynjsimpson on 2006-11-01
Hello,

I have searched this foruum for a solution for this but the first answer to did work and the second had no reply.

I read instructions on how to upgrade to Edgy Eft "gksudo "update-manager -c -d"" and followed instructions precisely however after downloading all necessary files it moved onto installing updates i recieved an error on a package called "failed in buffer_read(fd)".

I tried again and it failed again. 

After rebooting i noticed i had several hundred updates so attempted to do them, but again it failed with the same error.

After browsing around for some answers i checked my sources.list and everything had changed to "edgy" so i did a find replace back to "dapper" and rebooted.

I made sure the system was up to date and it was and attempted again but to no avail.

Now i really dislike long posts including long terminal dumps but if it helps here goes.

I have also tried removing all cached files in the archives of apt.

This first is from the sources.list back to orginal all with dapper.

> admin@square:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  libmagick9 libruby1.8 ruby1.8 screen
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3436kB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/screen_4.0.2-4.1ubuntu5.6.06_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libgcj7-jar': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/screen_4.0.2-4.1ubuntu5.6.06_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


Ok now i really can do anything in terms of updating.

I run gksudo "update-manager -c -d" and i get the error "Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) MD5Sum mismatch"

Any ideas would be appreciated. I have been using ubuntu as my first linux introduction and have picked it up very quickly within three months. Thanks Guys.

---

### Post by dgandhi on 2006-11-04
I have the same problem after update, only i have it with libnss3, and any attempt to install or remove anything, even libnss3 results in the same issue.

I have tracked it down all the way to dpkg, wich is the program from which the error originates. dpkg will not even allow a reinstall of the offending package. 

Does any body know:

1) a back end (dpkg) fix for this
2) which ubuntu package SHOULD catch/fix this error, to which we can submit a bug report.

TIA

---

