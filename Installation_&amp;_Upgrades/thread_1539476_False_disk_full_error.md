---
title: "False disk full error"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by musashi39 on 2010-07-26
I run apt-get upgrade and get
> Preconfiguring packages ...
(Reading database ... 78720 files and directories currently installed.)
Preparing to replace apt 0.7.25.3ubuntu9 (using .../apt_0.7.25.3ubuntu9.1_i386.deb) ...
Unpacking replacement apt ...
dpkg: error processing /var/cache/apt/archives/apt_0.7.25.3ubuntu9.1_i386.deb (--unpack):
 unable to create `/usr/share/locale/dz/LC_MESSAGES/apt.mo.dpkg-new' (while processing `./usr/share/locale/dz/LC_MESSAGES/apt.mo'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/apt_0.7.25.3ubuntu9.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have 10.04 server installed and df -h returns:
> Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              712G  385G  292G  57% /
none                  1.5G  272K  1.5G   1% /dev
none                  1.5G     0  1.5G   0% /dev/shm
none                  1.5G  352K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
none                  712G  385G  292G  57% /var/lib/ureadahead/debugfs
/dev/sda2              23G  217M   21G   2% /boot


---

### Post by musashi39 on 2010-07-27
Not sure what happened but every thing deteriorated very quickly. I started getting device full errors everywhere. Maybe my harddrive crashed (i'm using a different one now) but I did a complete reinstall. Thankfully I had backups!

---

