---
title: "Edgy to Fiesty: do-release-upgrade aborts itself"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by dudinatrix on 2007-04-23
I'm on Ubuntu Edgy Server (no GUI). Just upgraded from Dapper. Now I'm trying to upgrade to Feisty. Following the instructions here [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```It appears to start correctly, hitting the repositories for Edgy, then Feisty. But then it aborts itself. Here's the complete output:

```
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tools
[100%] 66.3kB/s 0s
Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done http://security.ubuntu.com edgy-security Release.gpg
Done http://archive.ubuntu.com edgy Release.gpg
Done http://archive.ubuntu.com edgy-proposed Release.gpg
Hit http://security.ubuntu.com edgy-security Release
Done http://archive.ubuntu.com edgy-updates Release.gpg
Done http://archive.ubuntu.com edgy-backports Release.gpg
Hit http://archive.ubuntu.com edgy Release
Hit http://archive.ubuntu.com edgy-proposed Release
Hit http://archive.ubuntu.com edgy-updates Release
Hit http://archive.ubuntu.com edgy-backports Release
Done http://security.ubuntu.com edgy-security Release
Done http://archive.canonical.com edgy-commercial Release.gpg
Done http://archive.ubuntu.com edgy Release
Hit http://security.ubuntu.com edgy-security/main Packages
Hit http://archive.canonical.com edgy-commercial Release
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Done http://archive.ubuntu.com edgy-updates Release
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://security.ubuntu.com edgy-security/universe Sources
Hit http://security.ubuntu.com edgy-security/multiverse Sources
Done http://archive.ubuntu.com edgy-backports Release
Done http://archive.canonical.com edgy-commercial Release
Hit http://archive.ubuntu.com edgy/main Sources
Hit http://archive.ubuntu.com edgy/restricted Sources
Hit http://archive.ubuntu.com edgy/universe Sources
Hit http://archive.ubuntu.com edgy/multiverse Sources
Hit http://archive.canonical.com edgy-commercial/main Packages
Done http://archive.ubuntu.com edgy-proposed Release
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/universe Packages
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://archive.ubuntu.com edgy-updates/main Sources
Hit http://archive.ubuntu.com edgy-updates/restricted Sources
Hit http://archive.ubuntu.com edgy-updates/universe Sources
Hit http://archive.ubuntu.com edgy-updates/multiverse Sources
Hit http://archive.ubuntu.com edgy-backports/main Packages
Done http://archive.ubuntu.com edgy-proposed Release
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com edgy-backports/main Sources
Hit http://archive.ubuntu.com edgy-backports/restricted Sources
Hit http://archive.ubuntu.com edgy-backports/universe Sources
Hit http://archive.ubuntu.com edgy-backports/multiverse Sources
Hit http://archive.ubuntu.com edgy-proposed/main Packages
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages
Hit http://archive.ubuntu.com edgy-proposed/universe Packages
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages
Done downloading

Updating repository information
WARNING: Failed to read mirror file
Done http://archive.canonical.com feisty-commercial Release.gpg
Done http://archive.ubuntu.com feisty Release.gpg
Done http://archive.ubuntu.com feisty-proposed Release.gpg
Done http://archive.ubuntu.com feisty-updates Release.gpg
Done http://archive.ubuntu.com feisty-backports Release.gpg
Done http://security.ubuntu.com feisty-security Release.gpg
Hit http://archive.canonical.com feisty-commercial Release
Hit http://archive.ubuntu.com feisty Release
Hit http://archive.ubuntu.com feisty-proposed Release
Hit http://security.ubuntu.com feisty-security Release
Hit http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty-backports Release
Done http://archive.canonical.com feisty-commercial Release
Done http://archive.ubuntu.com feisty Release
Hit http://archive.canonical.com feisty-commercial/main Packages
Hit http://archive.ubuntu.com feisty/main Packages
Done http://security.ubuntu.com feisty-security Release
Hit http://archive.ubuntu.com feisty/restricted Packages
Hit http://archive.ubuntu.com feisty/universe Packages
Hit http://archive.ubuntu.com feisty/multiverse Packages
Hit http://archive.ubuntu.com feisty/main Sources
Hit http://security.ubuntu.com feisty-security/main Packages
Done http://archive.ubuntu.com feisty-backports Release
Hit http://archive.ubuntu.com feisty/restricted Sources
Hit http://archive.ubuntu.com feisty/universe Sources
Hit http://archive.ubuntu.com feisty/multiverse Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Done http://archive.ubuntu.com feisty-proposed Release
Done http://archive.ubuntu.com feisty-proposed Release
Done http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty-backports/main Packages
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://archive.ubuntu.com feisty-backports/main Sources
Hit http://archive.ubuntu.com feisty-backports/restricted Sources
Hit http://archive.ubuntu.com feisty-backports/universe Sources
Hit http://archive.ubuntu.com feisty-backports/multiverse Sources
Done http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty-proposed/main Packages
Hit http://archive.ubuntu.com feisty-proposed/restricted Packages
Hit http://archive.ubuntu.com feisty-proposed/universe Packages
Hit http://archive.ubuntu.com feisty-proposed/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/main Packages
Hit http://archive.ubuntu.com feisty-updates/restricted Packages
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/main Sources
Hit http://archive.ubuntu.com feisty-updates/restricted Sources
Hit http://archive.ubuntu.com feisty-updates/universe Sources
Hit http://archive.ubuntu.com feisty-updates/multiverse Sources
Done downloading

Checking package manager
Reading package lists: Donem feisty-commercial/main Packages: 97
Reading state information: Done
Reading state information: Done
: 99

Asking for confirmation

Restoring original system state

Aborting
Reading package lists: Donem edgy-commercial/main Packages: 97
Reading state information: Done
Reading state information: Done
Reading state information: Done

```Here is the log output (/var/log/dist-upgrade/main.log):
```

2007-04-23 09:11:52,052 INFO release-upgrader version '0.59.20' started
2007-04-23 09:11:52,496 DEBUG lsb-release: 'edgy'
2007-04-23 09:11:52,497 DEBUG _pythonSymlinkCheck run
2007-04-23 09:13:55,524 DEBUG Foreign:
2007-04-23 09:13:55,583 DEBUG Obsolete: webmin-status slang1a-utf8 libmysqlclient12 webmin-mysql webmin-samba linux                                          -image-2.6.10-5-386 lshw-common linux-restricted-modules-2.6.15-25-386 webmin-usermin webmin-core linux-image-2.6.1                                          5-28-386 webmin-quota webmin-inetd webmin-postfix webmin libdevmapper1.00 libdevmapper1.01 linux-restricted-modules                                          -2.6.12-10-386 libiw27 libgnutls11 webmin-mailboxes webmin-apache webmin-lpadmin linux-restricted-modules-2.6.15-28                                          -386 proftpd-common libdns20 libparted1.6-13 php4-universe-common libpoppler0c2 libcupsys2-gnutls10 webmin-proftpd                                           liboggflac1 usermin python2.4-clearsilver libparted1.6-12 ubuntu-base linux-image-2.6.15-25-386 webmin-updown linux                                          -restricted-modules-2.6.10-5-386 webmin-procmail webmin-htaccess libsysfs1 libisc7 webcdwriter libflac6 liblwres1 l                                          ibdirectfb-0.9-22 webmin-grub linux-image-2.6.12-10-386 libisc9 libdns16
2007-04-23 09:13:55,624 DEBUG updateSourcesList()
2007-04-23 09:13:55,963 DEBUG rewriteSourcesList()
2007-04-23 09:13:55,997 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiv                                          erse'
2007-04-23 09:13:55,998 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multivers                                          e' updated to new dist
2007-04-23 09:13:55,999 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe mu                                          ltiverse'
2007-04-23 09:13:55,999 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multi                                          verse' updated to new dist
2007-04-23 09:13:56,000 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted univer                                          se multiverse'
2007-04-23 09:13:56,001 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted universe                                           multiverse' updated to new dist
2007-04-23 09:13:56,002 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted univers                                          e multiverse'
2007-04-23 09:13:56,003 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe m                                          ultiverse' updated to new dist
2007-04-23 09:13:56,003 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted uni                                          verse multiverse'
2007-04-23 09:13:56,004 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted univer                                          se multiverse' updated to new dist
2007-04-23 09:13:56,005 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu edgy-security main restricted unive                                          rse multiverse'
2007-04-23 09:13:56,006 DEBUG entry 'deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe                                           multiverse' updated to new dist
2007-04-23 09:13:56,007 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted u                                          niverse multiverse'
2007-04-23 09:13:56,008 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted univ                                          erse multiverse' updated to new dist
2007-04-23 09:13:56,008 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted unive                                          rse multiverse'
2007-04-23 09:13:56,009 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe                                           multiverse' updated to new dist
2007-04-23 09:13:56,010 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted u                                          niverse multiverse'
2007-04-23 09:13:56,011 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted univ                                          erse multiverse' updated to new dist
2007-04-23 09:13:56,012 DEBUG examining: 'deb http://archive.canonical.com/ubuntu edgy-commercial main'
2007-04-23 09:13:56,013 DEBUG entry 'deb http://archive.canonical.com/ubuntu feisty-commercial main' updated to new                                           dist
2007-04-23 09:14:19,105 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may                                           be caused by held packages.'

```"This may be caused by held packages."? Any idea how to get around this?

---

