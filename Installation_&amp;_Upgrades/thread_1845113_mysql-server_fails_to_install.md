---
title: "mysql-server fails to install"
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by thewinchester on 2011-09-16
Ok, noob to this stuff - so please be gentle.

Natty 64-bit system, attempting to install all the pre-reqs I need for SugarCRM. Sadly, APT is giving me a real headache with mysql-server-5.1 and refuses to install it.

Have stepped through apt-get clean all/update/upgrade, same result.

.postrm and .list files related to offending package cleaned out of /var/lib/dpkg/info/, same result.

Also, [per this post]("http://ubuntuforums.org/showpost.php?p=7840032&postcount=6"), no older version of /var/lib/dpkg/info exists.

If anyone can help drag me out of this never-ending cycle of fail, it would be greatly appreciated.

Error output as follows:

```

root@grill:/var/lib/dpkg/info# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  mysql-server-5.1
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 6,386 kB of archives.
After this operation, 14.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 ftp://ftp.iinet.net.au/pub/ubuntu/ natty/main mysql-server-5.1 amd64 5.1.54-1ubuntu4 [6,386 kB]
Fetched 6,386 kB in 5s (1,271 kB/s)           
debconf: Perl may be unconfigured (Unrecognized character \x08 in column 1 at /usr/share/perl5/Debconf/ConfModule.pm line 529.
Compilation failed in require at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
Compilation failed in require at (eval 1) line 8.
BEGIN failed--compilation aborted at (eval 1) line 8.
) -- aborting
(Reading database ... 
dpkg: warning: files list file for package `mysql-client-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-server' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-server-core-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-server-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-client-core-5.1' missing, assuming package has no files currently installed.
(Reading database ... 236032 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.54-1ubuntu4 (using .../mysql-server-5.1_5.1.54-1ubuntu4_amd64.deb) ...
Unrecognized character \x08 in column 1 at /usr/share/perl5/Debconf/ConfModule.pm line 529.
Compilation failed in require at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
Compilation failed in require at /usr/share/debconf/frontend line 8.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 8.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.1_5.1.54-1ubuntu4_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 9
Unrecognized character \x08 in column 1 at /usr/share/perl5/Debconf/ConfModule.pm line 529.
Compilation failed in require at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
Compilation failed in require at /usr/share/debconf/frontend line 8.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 8.
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.1_5.1.54-1ubuntu4_amd64.deb
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by thewinchester on 2011-09-17
Managed to find the solution to at least get past the problem whereby this was preventing installation of any other packages:

[http://ubuntuforums.org/showpost.php?p=2241542&postcount=15](http://ubuntuforums.org/showpost.php?p=2241542&postcount=15)

---

