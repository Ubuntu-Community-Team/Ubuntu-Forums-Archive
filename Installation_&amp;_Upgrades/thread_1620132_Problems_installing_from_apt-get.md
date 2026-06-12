---
title: "Problems installing from apt-get"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by dgohn on 2010-11-12
For some reason any time I try to install anything now with apt-get it fails.  Regardless of what it is I am trying to install.  Can anyone possibly tell me what is causing this?  Below is the blurb...



```


root@randomserver:/# apt-get install nano
Reading package lists... Done
Building dependency tree
Reading state information... Done
nano is already the newest version.
The following packages will be REMOVED:
  dovecot-common lsb-release openssl-blacklist postfix postgresql-common python python-central python-dev python-subversion python-support python2.5-dev sendmail-base sensible-mda ssl-cert
  svn-load svn-workbench svnmailer ufw update-manager-core vsftpd weather-util
0 upgraded, 0 newly installed, 21 to remove and 87 not upgraded.
21 not fully installed or removed.
After this operation, 42.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 74567 files and directories currently installed.)
Removing dovecot-common ...
dpkg: error processing dovecot-common (--remove):
 cannot remove `/usr/bin/convert-tool': Permission denied
Removing update-manager-core ...
dpkg: error processing update-manager-core (--remove):
 cannot remove `/usr/bin/do-release-upgrade': Permission denied
Removing lsb-release ...
dpkg: error processing lsb-release (--remove):
 cannot remove `/usr/bin/lsb_release': Permission denied
Removing postgresql-common ...
dpkg: error processing postgresql-common (--remove):
 cannot remove `/usr/sbin/pg_maintenance': Permission denied
Removing vsftpd ...
dpkg: error processing vsftpd (--remove):
 cannot remove `/usr/sbin/vsftpd': Permission denied
Removing sensible-mda ...
dpkg: error processing sensible-mda (--remove):
 cannot remove `/usr/sbin/sensible-mda': Permission denied
Removing postfix ...
dpkg: error processing postfix (--remove):
 cannot remove `/usr/bin/mailq': Permission denied
Removing ssl-cert ...
dpkg: error processing ssl-cert (--remove):
 cannot remove `/usr/sbin/make-ssl-cert': Permission denied
Removing openssl-blacklist ...
dpkg: error processing openssl-blacklist (--remove):
 cannot remove `/usr/bin/openssl-vulnkey': Permission denied
Removing ufw ...
dpkg: error processing ufw (--remove):
 cannot remove `/usr/sbin/ufw': Permission denied
Removing svnmailer ...
dpkg: error processing svnmailer (--remove):
 cannot remove `/usr/bin/svn-mailer': Permission denied
Removing python-subversion ...
dpkg: error processing python-subversion (--remove):
 cannot remove `/usr/bin/svnshell': Permission denied
Removing weather-util ...
dpkg: error processing weather-util (--remove):
 cannot remove `/usr/bin/weather': Permission denied
Removing svn-workbench ...
dpkg: error processing svn-workbench (--remove):
 cannot remove `/usr/bin/svn-workbench': Permission denied
Removing python-central ...
dpkg: error processing python-central (--remove):
 cannot remove `/usr/bin/dh_pycentral': Permission denied
Removing svn-load ...
dpkg: error processing svn-load (--remove):
 cannot remove `/usr/bin/svn-load': Permission denied
Removing python-support ...
dpkg: error processing python-support (--remove):
 cannot remove `/usr/bin/dh_pysupport': Permission denied
Removing python-dev ...
dpkg: error processing python-dev (--remove):
 cannot remove `/usr/bin/python-config': Permission denied
Removing python ...
dpkg: error processing python (--remove):
 cannot remove `/usr/bin/pdb': Permission denied
Removing python2.5-dev ...
dpkg: error processing python2.5-dev (--remove):
 cannot remove `/usr/bin/python2.5-config': Permission denied
Removing sendmail-base ...
dpkg: error processing sendmail-base (--remove):
 cannot remove `/usr/sbin/sendmailconfig': Permission denied
Errors were encountered while processing:
 dovecot-common
 update-manager-core
 lsb-release
 postgresql-common
 vsftpd
 sensible-mda
 postfix
 ssl-cert
 openssl-blacklist
 ufw
 svnmailer
 python-subversion
 weather-util
 svn-workbench
 python-central
 svn-load
 python-support
 python-dev
 python
 python2.5-dev
 sendmail-base





```

Thanks in advance for any help!

---

### Post by spiky001 on 2010-11-12
```
sudo apt-get 
```

---

### Post by dgohn on 2010-11-12
Thanks but that doesn't work either.  First thing I tried.  Not sure why this is happening.

```



root@randomserver:/# sudo apt-get install nano
Reading package lists... Done
Building dependency tree
Reading state information... Done
nano is already the newest version.
The following packages will be REMOVED:
  dovecot-common lsb-release openssl-blacklist postfix postgresql-common python python-central python-dev python-subversion python-support python2.5-dev sendmail-base sensible-mda ssl-cert
  svn-load svn-workbench svnmailer ufw update-manager-core vsftpd weather-util
0 upgraded, 0 newly installed, 21 to remove and 87 not upgraded.
21 not fully installed or removed.
After this operation, 42.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 74567 files and directories currently installed.)
Removing dovecot-common ...
dpkg: error processing dovecot-common (--remove):
 cannot remove `/usr/bin/convert-tool': Permission denied
Removing update-manager-core ...
dpkg: error processing update-manager-core (--remove):
 cannot remove `/usr/bin/do-release-upgrade': Permission denied
Removing lsb-release ...
dpkg: error processing lsb-release (--remove):
 cannot remove `/usr/bin/lsb_release': Permission denied
Removing postgresql-common ...
dpkg: error processing postgresql-common (--remove):
 cannot remove `/usr/sbin/pg_maintenance': Permission denied
Removing vsftpd ...
dpkg: error processing vsftpd (--remove):
 cannot remove `/usr/sbin/vsftpd': Permission denied
Removing sensible-mda ...
dpkg: error processing sensible-mda (--remove):
 cannot remove `/usr/sbin/sensible-mda': Permission denied
Removing postfix ...
dpkg: error processing postfix (--remove):
 cannot remove `/usr/bin/mailq': Permission denied
Removing ssl-cert ...
dpkg: error processing ssl-cert (--remove):
 cannot remove `/usr/sbin/make-ssl-cert': Permission denied
Removing openssl-blacklist ...
dpkg: error processing openssl-blacklist (--remove):
 cannot remove `/usr/bin/openssl-vulnkey': Permission denied
Removing ufw ...
dpkg: error processing ufw (--remove):
 cannot remove `/usr/sbin/ufw': Permission denied
Removing svnmailer ...
dpkg: error processing svnmailer (--remove):
 cannot remove `/usr/bin/svn-mailer': Permission denied
Removing python-subversion ...
dpkg: error processing python-subversion (--remove):
 cannot remove `/usr/bin/svnshell': Permission denied
Removing weather-util ...
dpkg: error processing weather-util (--remove):
 cannot remove `/usr/bin/weather': Permission denied
Removing svn-workbench ...
dpkg: error processing svn-workbench (--remove):
 cannot remove `/usr/bin/svn-workbench': Permission denied
Removing python-central ...
dpkg: error processing python-central (--remove):
 cannot remove `/usr/bin/dh_pycentral': Permission denied
Removing svn-load ...
dpkg: error processing svn-load (--remove):
 cannot remove `/usr/bin/svn-load': Permission denied
Removing python-support ...
dpkg: error processing python-support (--remove):
 cannot remove `/usr/bin/dh_pysupport': Permission denied
Removing python-dev ...
dpkg: error processing python-dev (--remove):
 cannot remove `/usr/bin/python-config': Permission denied
Removing python ...
dpkg: error processing python (--remove):
 cannot remove `/usr/bin/pdb': Permission denied
Removing python2.5-dev ...
dpkg: error processing python2.5-dev (--remove):
 cannot remove `/usr/bin/python2.5-config': Permission denied
Removing sendmail-base ...
dpkg: error processing sendmail-base (--remove):
 cannot remove `/usr/sbin/sendmailconfig': Permission denied
Errors were encountered while processing:
 dovecot-common
 update-manager-core
 lsb-release
 postgresql-common
 vsftpd
 sensible-mda
 postfix
 ssl-cert
 openssl-blacklist
 ufw
 svnmailer
 python-subversion
 weather-util
 svn-workbench
 python-central
 svn-load
 python-support
 python-dev
 python
 python2.5-dev
 sendmail-base
E: Sub-process /usr/bin/dpkg returned an error code (1)





```

---

### Post by garvinrick4 on 2010-11-12
You are already in root and nano is the latest package already installed.
What happens if you get out  of root for a moment: IF for some reason you like root leave off the sudo. exit gets out of root
```
exit
``````
sudo dpkg --configure -a
``````
sudo apt-get install aptitude
``````
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by dgohn on 2010-11-12
Doesn't seem to have worked.



```


root@randomserver:/# dpkg --configure -a
root@randomserver:/# apt-get install aptitude
Reading package lists... Done
Building dependency tree
Reading state information... Done
aptitude is already the newest version.
The following packages will be REMOVED:
  dovecot-common lsb-release openssl-blacklist postfix postgresql-common
  python python-central python-dev python-subversion python-support
  python2.5-dev sendmail-base sensible-mda ssl-cert svn-load svn-workbench
  svnmailer ufw update-manager-core vsftpd weather-util
0 upgraded, 0 newly installed, 21 to remove and 87 not upgraded.
21 not fully installed or removed.
After this operation, 42.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 74567 files and directories currently installed.)
Removing dovecot-common ...
dpkg: error processing dovecot-common (--remove):
 cannot remove `/usr/bin/convert-tool': Permission denied
Removing update-manager-core ...
dpkg: error processing update-manager-core (--remove):
 cannot remove `/usr/bin/do-release-upgrade': Permission denied
Removing lsb-release ...
dpkg: error processing lsb-release (--remove):
 cannot remove `/usr/bin/lsb_release': Permission denied
Removing postgresql-common ...
dpkg: error processing postgresql-common (--remove):
 cannot remove `/usr/sbin/pg_maintenance': Permission denied
Removing vsftpd ...
dpkg: error processing vsftpd (--remove):
 cannot remove `/usr/sbin/vsftpd': Permission denied
Removing sensible-mda ...
dpkg: error processing sensible-mda (--remove):
 cannot remove `/usr/sbin/sensible-mda': Permission denied
Removing postfix ...
dpkg: error processing postfix (--remove):
 cannot remove `/usr/bin/mailq': Permission denied
Removing ssl-cert ...
dpkg: error processing ssl-cert (--remove):
 cannot remove `/usr/sbin/make-ssl-cert': Permission denied
Removing openssl-blacklist ...
dpkg: error processing openssl-blacklist (--remove):
 cannot remove `/usr/bin/openssl-vulnkey': Permission denied
Removing ufw ...
dpkg: error processing ufw (--remove):
 cannot remove `/usr/sbin/ufw': Permission denied
Removing svnmailer ...
dpkg: error processing svnmailer (--remove):
 cannot remove `/usr/bin/svn-mailer': Permission denied
Removing python-subversion ...
dpkg: error processing python-subversion (--remove):
 cannot remove `/usr/bin/svnshell': Permission denied
Removing weather-util ...
dpkg: error processing weather-util (--remove):
 cannot remove `/usr/bin/weather': Permission denied
Removing svn-workbench ...
dpkg: error processing svn-workbench (--remove):
 cannot remove `/usr/bin/svn-workbench': Permission denied
Removing python-central ...
dpkg: error processing python-central (--remove):
 cannot remove `/usr/bin/dh_pycentral': Permission denied
Removing svn-load ...
dpkg: error processing svn-load (--remove):
 cannot remove `/usr/bin/svn-load': Permission denied
Removing python-support ...
dpkg: error processing python-support (--remove):
 cannot remove `/usr/bin/dh_pysupport': Permission denied
Removing python-dev ...
dpkg: error processing python-dev (--remove):
 cannot remove `/usr/bin/python-config': Permission denied
Removing python ...
dpkg: error processing python (--remove):
 cannot remove `/usr/bin/pdb': Permission denied
Removing python2.5-dev ...
dpkg: error processing python2.5-dev (--remove):
 cannot remove `/usr/bin/python2.5-config': Permission denied
Removing sendmail-base ...
dpkg: error processing sendmail-base (--remove):
 cannot remove `/usr/sbin/sendmailconfig': Permission denied
Errors were encountered while processing:
 dovecot-common
 update-manager-core
 lsb-release
 postgresql-common
 vsftpd
 sensible-mda
 postfix
 ssl-cert
 openssl-blacklist
 ufw
 svnmailer
 python-subversion
 weather-util
 svn-workbench
 python-central
 svn-load
 python-support
 python-dev
 python
 python2.5-dev
 sendmail-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@randomserver:/# aptitude update && sudo aptitude safe-upgrade
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages have unmet dependencies:
  update-manager-core: Depends: python-apt (>= 0.7.4ubuntu5) but it is not insta                                                                                                                     llable
                       Depends: python-gnupginterface but it is not installable
  svn-workbench: Depends: python-svn (>= 1.5.2) but it is not installable
                 Depends: python-wxgtk2.6 but it is not installable
  svn-load: Depends: python-svn but it is not installable



```

---

### Post by ptantiku on 2010-11-12
why it's getting permission denied, even with root access?  
maybe /usr is mounting with readonly option?

---

### Post by garvinrick4 on 2010-11-12
Here are the 3 packages with unmet dependencys:
```
rick@rick-HP-G71-Notebook-PC:/$ aptitude show svn-load
Package: svn-load                        
State: not installed
Version: 1.2-1
Priority: extra
Section: universe/devel
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 61.4 k
Depends: python, python-svn
Description: An enhanced import facility for Subversion
 svn-load is a free replacement for svn_load_dirs, an enhanced import facility
 for Subversion. 
 
 This utility will commit a single changeset that alters a repository subtree to
 match a local directory. It detects filenames that have been removed or
 created, and uses this knowledge to prompt the user about file and directory
 movements within the subtree. An automatic tagging option is also supported. 
 
 svn-load is well suited for vendor branch maintenance, where external source is
 routinely imported and merged.

rick@rick-HP-G71-Notebook-PC:/$ aptitude show svn-workbench
Package: svn-workbench                   
State: not installed
Version: 1.6.2-1.1
Priority: optional
Section: universe/devel
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,749 k
Depends: python, python-central (>= 0.6.11), python-svn (>= 1.7.1),
         python-wxgtk2.8
Description: A Workbench for Subversion
 pysvn-workbench is a workbench (graphical client) for the Subversion revision
 control system, written in the Python language.

rick@rick-HP-G71-Notebook-PC:/$ aptitude show update-manager-core
Package: update-manager-core             
State: installed
Automatically installed: no
Version: 1:0.145.1
Priority: standard
Section: admin
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 1,217 k
Depends: python (< 2.8), python (>= 2.6), python-central (>= 0.6.11), python2.7,
         python-apt (>= 0.7.13.4ubuntu3), lsb-release, python-gnupginterface
Recommends: libpam-modules (>= 1.0.1-9ubuntu3)
Conflicts: computer-janitor (<= 1.11-0ubuntu1), update-manager (< 1:0.93.7)
Replaces: update-manager (< 1:0.93.7)
Description: manage release upgrades
 This is the core of update-manager and the release upgrader

rick@rick-HP-G71-Notebook-PC:/$ 

```

---

