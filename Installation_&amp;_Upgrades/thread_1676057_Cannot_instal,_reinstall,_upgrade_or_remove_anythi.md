---
title: "Cannot instal, reinstall, upgrade or remove anything  anymore"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by santana007 on 2011-01-26
I recently did a "*Complete Removal*" (by accident) of Python :oops: :razz: :-({|=. I'm using Maverick (10.10). Everything disappeared i.e. Desktop, applications etc. I managed to get it all restored and working again but now I can't install or remove etc just like the title says. Update Manager wants to do its thing but can't. The issue seems to center around an upgrade of Samba. I get the message that the package is badly broken and should be reinstalled before removal. However I can't do this. I've tried a number of different commands in  Terminal such as --fix-broken and --fix-missing, etc. When I run  ***sudo apt-get install -f***, I get this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-libuser libuser1 asterisk-sounds-main
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  samba
Suggested packages:
  ldb-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.
11 not fully installed or removed.
Need to get 0B/7,450kB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (Can't locate File/Spec.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/IO/File.pm line 12.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO/File.pm line 12.
Compilation failed in require at /usr/share/perl/5.10/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
Setting up debconf (1.5.32ubuntu3) ...
Can't locate File/Spec.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/IO/File.pm line 12.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO/File.pm line 12.
Compilation failed in require at /usr/share/perl/5.10/FileHandle.pm line 9.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing debconf (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 debconf
E: Sub-process /usr/bin/dpkg returned an error code (1)
```And when I try ***sudo dpkg --configure -a***, I get this:

```
Setting up debconf (1.5.32ubuntu3) ...
Can't locate File/Spec.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/IO/File.pm line 12.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO/File.pm line 12.
Compilation failed in require at /usr/share/perl/5.10/FileHandle.pm line 9.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing debconf (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of man-db:
 man-db depends on debconf (>= 1.2.0) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing man-db (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba-common:
 samba-common depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing samba-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.5.4~dfsg-1ubuntu8.2); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ushare:
 ushare depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing ushare (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ufw:
 ufw depends on debconf; however:
  Package debconf is not configured yet.
 ufw depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing ufw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cifs-utils:
 cifs-utils depends on samba-common; however:
  Package samba-common is not configured yet.
dpkg: error processing cifs-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba-common (= 2:3.5.4~dfsg-1ubuntu8.2); however:
  Package samba-common is not configured yet.
dpkg: error processing winbind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbfs:
 smbfs depends on cifs-utils (= 2:4.5-2); however:
  Package cifs-utils is not configured yet.
dpkg: error processing smbfs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 debconf
 man-db
 samba-common
 smbclient
 ushare
 ufw
 samba-common-bin
 cifs-utils
 winbind
 smbfs
```I know I can backup my apps and data and reinstall the entire system and start from square one but would there be any easier fix? 

Thanks in advanced for any suggestions.

---

### Post by zvacet on 2011-01-29
```
sudo dpkg --configure  debconf
sudo dpkg --configure samba-common
```

or try to install that packages and see if that helps.

---

### Post by santana007 on 2011-01-29
> **zvacet said:**
> ```
sudo dpkg --configure  debconf
sudo dpkg --configure samba-common
```or try to install that packages and see if that helps.

Thanks for the reply but still no go. When I try
sudo dpkg --configure debconf, I receive:

```
Setting up debconf (1.5.32ubuntu3) ...
Can't locate File/Spec.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/IO/File.pm line 12.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO/File.pm line 12.
Compilation failed in require at /usr/share/perl/5.10/FileHandle.pm line 9.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing debconf (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 debconf

```When I try sudo dpkg --configure samba-common, I get

```
dpkg: dependency problems prevent configuration of samba-common:
 samba-common depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not configured yet.
  Package debconf-2.0 is not installed.
  Package debconf which provides debconf-2.0 is not configured yet.
dpkg: error processing samba-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common

```I will keep trying. The above readout is a new one and may provide some clues. If all else fails, I will reinstall.
Thanks again for your help.

---

### Post by zvacet on 2011-01-29
Maybe [this]("http://ubuntuforums.org/showthread.php?t=863056") or [this]("http://www.khattam.info/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error-2009-08-04.html") can help you.

---

