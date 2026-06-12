---
title: "Computer crashed-now apt won't work"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by Zeromaru on 2008-05-05
I turned on my laptop this morning and found there were some updates, mostly for apport and evolution-data-server. During the upgrade however, the computer crashed.

Upon restart, I tried running it again, and got the error
```
 files list file for package `libecal1.2-7' is missing final newline
```

After much research I discovered fixing this was a matter of deleting /var/lib/dpkg/info/libecal1.2-7.list, purging the package, then reinstalling it. However, upon running apt-get again to purge, I get the following error
```
 files list file for package `libedata-book1.2-2' is missing final newline
```

Note I've tried adding a newline to the corresponding file, no luck, though comparing it to other .list files shows something isn't right

```
Package: libecal1.2-7
Status: install ok unpacked
Priority: optional
Section: libs
Installed-Size: 716
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Source: evolution-data-server
Version: 2.22.1-0ubuntu2.1
Config-Version: 2.22.1-0ubuntu2
Depen
```

Other .list files in the same directory have lists of files.

I've considered just removing all the troublesome .list files and purging the packages as it's been suggested, however apt-get preliminaries shows that such and action will thoroughly wreck my system by removing a vast number of packages (pretty much all of Gnome). I'd rather not do that, nor do I prefer to format and start fresh (considering I've done that twice in the last week-once to install 8.04, again to install 7.10 and then upgrade so I'd have the old kernel as the new one doesn't get along with wpa_supplicant and the eeemadwifi drivers).

Any help would be so greatly appreciated.

---

### Post by Pumalite on 2008-05-05
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
Post the output. Good luck.

---

### Post by Zeromaru on 2008-05-05
```
root@madhatter:~# dpkg --configure -a
root@madhatter:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgdata1.2-1 libgdata-google1.2-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
root@madhatter:~# apt-get clean
root@madhatter:~# apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_CA
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_CA
Ign http://archive.ubuntu.com hardy/restricted Translation-en_CA
Ign http://archive.ubuntu.com hardy/universe Translation-en_CA
Hit http://archive.canonical.com hardy Release
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_CA
Hit http://archive.ubuntu.com hardy-updates Release.gpg
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_CA
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_CA
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_CA
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_CA
Hit http://archive.ubuntu.com hardy-security Release.gpg
Ign http://archive.ubuntu.com hardy-security/main Translation-en_CA
Hit http://archive.canonical.com hardy/partner Packages
Hit http://archive.canonical.com hardy/partner Sources
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_CA
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_CA
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_CA
Hit http://archive.ubuntu.com hardy-backports Release.gpg
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_CA
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_CA
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_CA
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_CA
Hit http://archive.ubuntu.com hardy Release
Hit http://archive.ubuntu.com hardy-updates Release
Hit http://archive.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com hardy-backports Release
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://archive.ubuntu.com hardy/restricted Sources
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/main Sources
Hit http://archive.ubuntu.com hardy-updates/restricted Sources
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Hit http://archive.ubuntu.com hardy-updates/universe Sources
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/universe Sources
Hit http://archive.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Sources
Hit http://archive.ubuntu.com hardy-backports/restricted Packages
Hit http://archive.ubuntu.com hardy-backports/main Packages
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://archive.ubuntu.com hardy-backports/universe Packages
Reading package lists... Done
root@madhatter:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apport apport-gtk evolution-data-server-common gtk2-engines-pixbuf hal
  libcamel1.2-11 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8
  libegroupwise1.2-13 libexchange-storage1.2-3 libgdata-google1.2-1
  libgdata1.2-1 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libhal-storage1
  libhal1 python-apport python-problem-report
23 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4911kB of archives.
After this operation, 12.3kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com hardy-updates/main python-problem-report 0.108.1 [58.3kB]
Get:2 http://archive.ubuntu.com hardy-updates/main python-apport 0.108.1 [56.6kB]
Get:3 http://archive.ubuntu.com hardy-updates/main apport 0.108.1 [105kB]
Get:4 http://archive.ubuntu.com hardy-updates/main apport-gtk 0.108.1 [54.9kB]
Get:5 http://archive.ubuntu.com hardy-updates/main evolution-data-server-common 2.22.1-0ubuntu2.1 [72.1kB]
Get:6 http://archive.ubuntu.com hardy-updates/main libgtk2.0-common 2.12.9-3ubuntu3 [304kB]
Get:7 http://archive.ubuntu.com hardy-updates/main gtk2-engines-pixbuf 2.12.9-3ubuntu3 [317kB]
Get:8 http://archive.ubuntu.com hardy-updates/main libgtk2.0-0 2.12.9-3ubuntu3 [2067kB]
Get:9 http://archive.ubuntu.com hardy-updates/main libhal1 0.5.11~rc2-1ubuntu8 [84.4kB]
Get:10 http://archive.ubuntu.com hardy-updates/main libhal-storage1 0.5.11~rc2-1ubuntu8 [22.5kB]
Get:11 http://archive.ubuntu.com hardy-updates/main hal 0.5.11~rc2-1ubuntu8 [420kB]
Get:12 http://archive.ubuntu.com hardy-updates/main libedataserver1.2-9 2.22.1-0ubuntu2.1 [112kB]
Get:13 http://archive.ubuntu.com hardy-updates/main libcamel1.2-11 2.22.1-0ubuntu2.1 [304kB]
Get:14 http://archive.ubuntu.com hardy-updates/main libebook1.2-9 2.22.1-0ubuntu2.1 [79.6kB]
Get:15 http://archive.ubuntu.com hardy-updates/main libecal1.2-7 2.22.1-0ubuntu2.1 [242kB]
Get:16 http://archive.ubuntu.com hardy-updates/main libedata-book1.2-2 2.22.1-0ubuntu2.1 [47.6kB]
Get:17 http://archive.ubuntu.com hardy-updates/main libedata-cal1.2-6 2.22.1-0ubuntu2.1 [57.1kB]
Get:18 http://archive.ubuntu.com hardy-updates/main libedataserverui1.2-8 2.22.1-0ubuntu2.1 [75.3kB]
Get:19 http://archive.ubuntu.com hardy-updates/main libegroupwise1.2-13 2.22.1-0ubuntu2.1 [105kB]
Get:20 http://archive.ubuntu.com hardy-updates/main libexchange-storage1.2-3 2.22.1-0ubuntu2.1 [119kB]
Get:21 http://archive.ubuntu.com hardy-updates/main libgdata1.2-1 2.22.1-0ubuntu2.1 [58.0kB]
Get:22 http://archive.ubuntu.com hardy-updates/main libgdata-google1.2-1 2.22.1-0ubuntu2.1 [12.7kB]
Get:23 http://archive.ubuntu.com hardy-updates/main libgtk2.0-bin 2.12.9-3ubuntu3 [137kB]
Fetched 4911kB in 48s (101kB/s)                                                
(Reading database ... dpkg: error processing /var/cache/apt/archives/python-problem-report_0.108.1_all.deb (--unpack):
 files list file for package `libedata-book1.2-2' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/python-problem-report_0.108.1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Pumalite on 2008-05-05
sudo apt-get clean was supposed to clean your archives. You could go there by gksudo nautilus and erase them by hand.

---

### Post by Zeromaru on 2008-05-05
apt-get clean DID remove the archives.

```
root@madhatter:~# cd /var/cache/apt/archives
root@madhatter:/var/cache/apt/archives# ls
apport_0.108.1_all.deb
apport-gtk_0.108.1_all.deb
evolution-data-server-common_2.22.1-0ubuntu2.1_all.deb
gtk2-engines-pixbuf_2.12.9-3ubuntu3_i386.deb
hal_0.5.11~rc2-1ubuntu8_i386.deb
libcamel1.2-11_2.22.1-0ubuntu2.1_i386.deb
libebook1.2-9_2.22.1-0ubuntu2.1_i386.deb
libecal1.2-7_2.22.1-0ubuntu2.1_i386.deb
libedata-book1.2-2_2.22.1-0ubuntu2.1_i386.deb
libedata-cal1.2-6_2.22.1-0ubuntu2.1_i386.deb
libedataserver1.2-9_2.22.1-0ubuntu2.1_i386.deb
libedataserverui1.2-8_2.22.1-0ubuntu2.1_i386.deb
libegroupwise1.2-13_2.22.1-0ubuntu2.1_i386.deb
libexchange-storage1.2-3_2.22.1-0ubuntu2.1_i386.deb
libgdata1.2-1_2.22.1-0ubuntu2.1_i386.deb
libgdata-google1.2-1_2.22.1-0ubuntu2.1_i386.deb
libgtk2.0-0_2.12.9-3ubuntu3_i386.deb
libgtk2.0-bin_2.12.9-3ubuntu3_all.deb
libgtk2.0-common_2.12.9-3ubuntu3_all.deb
libhal1_0.5.11~rc2-1ubuntu8_i386.deb
libhal-storage1_0.5.11~rc2-1ubuntu8_i386.deb
lock
partial
python-apport_0.108.1_all.deb
python-problem-report_0.108.1_all.deb
root@madhatter:/var/cache/apt/archives# apt-get clean
root@madhatter:/var/cache/apt/archives# ls
lock  partial
```

---

### Post by Pumalite on 2008-05-05
Remove this:
'python-problem-report_0.108.1_all.deb'

---

### Post by Zeromaru on 2008-05-05
No luck.

I checked more .list files in /var /lib/dpkg/info, and the ones corresponding to the problem packages are all weird, just like the ones I already posted about. I'm certain the solution lies in fixing these .list files, but I don't know how to go about it.

---

### Post by Pumalite on 2008-05-05
Check /var/lib/dpkg/status

---

### Post by Zeromaru on 2008-05-05
I don't know what you want me to check for, but the contents of the file appear to be a listing of all packages, and the problem .list files have the same format.

---

### Post by Pumalite on 2008-05-05
The good packages say: installed...ok...installed

---

### Post by Zeromaru on 2008-05-05
"install ok installed" on all the problem ones :S

---

### Post by Pumalite on 2008-05-05
This is a new one for me. Sorry. Wait for better help than I.
The other thing is a clean install, but wait a while because I don't have all the answers by any means.

---

### Post by ubuntu-freak on 2008-05-06
Perhaps you should just delete the troublesome .list files, then reboot into recovery mode and execute:
 
**sudo apt-get purge ubuntu-desktop && sudo apt-get install ubuntu-desktop**
 
That's all I can think of, short of a fresh install.
 
Nathan

---

### Post by sansloy on 2008-05-12
If you still have this problem, you might find this link useful:

[https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html)

1.  I ended up with three corrupt list files due to some problem with my / drive.  fsck found 3 blocks that had multiple claims and I replied "fix it", which resulted in corruption in three list files.

2.  I discovered the problem when attempting to install memtester package:

(Reading database ... dpkg: error processing /var/cache/apt/archives/memtester_2.93.1-3.1_i386.deb (--unpack):
 files list file for package `libuniconf4.2' is missing final newline

3.  Using the instructions at the above link, I was able reinstall libuniconf package.  However, the next attempt to install memtester ran into another bad list file (for ntfs-3g).  So, repeated reinstall instructions and attempted install of memtester until successful.

4.  Haven't encountered any problems with package installs since then.  YMMV.

Best of luck.

---

