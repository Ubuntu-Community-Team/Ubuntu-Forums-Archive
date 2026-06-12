---
title: "Errors were encountered - how do I get around it"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by maxweld on 2007-10-20
I am installing the ubuntu-desktop onto the Gutsy Server edition that I have just installed.

I get 
```
Errors were encountered while processing:
  /var/cache/apt/archives/gnome-user-guide_2.20.0+svn20071003ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How do I get around this little problem?

Thanks in advance

---

### Post by maxweld on 2007-10-20
I found a suggestion in another forum to run repeatedly the following commands.

sudo apt-get -f install 
sudo apt-get install pkgname 

It now seems that there are corruptions or problems with two files. I get the following messages

Unpacking gnome-user-guide (from .../gnome-user-guide_2.20.0+svn20071003ubuntu2_all.deb)
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/gnome-user-guide_2.20.0+svn20071003ubuntu2_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during './usr/share/gnome/help/system-admin-guide/C/system-admin-guide.pdf')

and 

Unpacking oppenoffice.org-core (from .../openoffice.org-core_1%3a2.3.0-1ubuntu5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/oppenoffice.org-core_1%3a2.3.0-1ubuntu5_i386.deb (--unpack)
 corrupted filesystem tarefile - corrupted package archive
dpkg-deb: subprocesses paste killed by signal (Broken pipe)

Then I get the usual 

Errors were encountered while processing:
 /var/cache/apt/archives/gnome-user-guide_2.20.0+svn20071003ubuntu2_all.deb 
 /var/cache/apt/archives/oppenoffice.org-core_1%3a2.3.0-1ubuntu5_i386.deb 
E: Sub-processes /usr/bin/dpkg returned an error code (1)

Any ideas what to do?

---

### Post by 52rockwell on 2007-10-21
I am getting a similar error after upgrading to 7.1 from Fiesty

Code:

Errors were encountered while processing:
  /var/cache/apt/archives/gnome-user-guide_2.20.0+svn20071003ubuntu2_all.deb

corrupted filesystem tarfile-corrupted package archive

---

### Post by maxweld on 2007-10-24
I managed to find another copy of this file, copied it to the machine and then ran 'apt-get -f install' and all worked fine.

---

### Post by grumps808 on 2007-10-29
If you are still having problems with gnome-user-guide_2.20.0+svn20071003ubuntu2_all.deb mainly 
```
dpkg: error processing gnome-user-guide (--configure):
 subprocess post-installation script returned error exit status 139
...
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Might want to try:
```
sudo apt-get install --reinstall scrollkeeper
```

---

### Post by jmcqueen on 2007-11-04
OpenOffice.org -calc is no longer available in my apps. When I try to install or attempt removal I get the following error. 

E: /var/cache/apt/archives/openoffice.org-calc_1%3a2.3.0-1ubuntu5_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libsc680li.so')

Any advice?

---

