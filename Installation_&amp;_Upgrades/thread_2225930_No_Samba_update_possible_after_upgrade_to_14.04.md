---
title: "No Samba update possible after upgrade to 14.04"
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by Eric_Damhuis on 2014-05-24
System tells me  to check for dependenties if  I want to run the update.
Because I cannot get on the network after the upgrade to 14.04


~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba-libs
The following NEW packages will be installed:
  samba-libs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0 B/4099 kB of archives.
After this operation, 18,3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 413027 files and directories currently installed.)
Preparing to unpack .../samba-libs_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_amd64.deb ...
secrets.tdb exists in /var/lib/samba and /var/lib/samba/private, aborting samba-libs preinst
rename one of them to allow the install/upgrade to continue
[http://bugs.debian.org/726472](http://bugs.debian.org/726472)
/var/lib/samba:
total 2208
drwxr-xr-x   7 root root         4096 mei 23 15:34 .
drwxr-xr-x  69 root root         4096 mei 23 15:33 ..
-rw-------   1 root root       421888 okt 19  2013 account_policy.tdb
-rw-------   1 root root          696 okt 19  2013 group_mapping.tdb
drwxr-x---   2 root root         4096 mei 19 21:46 ntp_signd
-rw-------   1 root root       421888 okt 19  2013 passdb.tdb
drwxr-xr-x   6 root root         4096 mei 19 21:46 private
-rw-------   1 root root       528384 nov  6  2013 registry.tdb
-rw-------   1 root root       430080 okt 19  2013 secrets.tdb
-rw-------   1 root root       421888 apr 16 12:49 share_info.tdb
drwxrwx---+  3 root    3000000   4096 okt 19  2013 sysvol
drwxrwx--T   2 root sambashare   4096 okt 20  2013 usershares
drwxr-x---   2 root root         4096 okt 20  2013 winbindd_privileged


/var/lib/samba/private:
total 10904
drwxr-xr-x 6 root root    4096 mei 19 21:46 .
drwxr-xr-x 7 root root    4096 mei 23 15:34 ..
-rw-r--r-- 1 root root    2270 okt 19  2013 dns_update_list
-rw------- 1 root root 1286144 okt 19  2013 hklm.ldb
-rw------- 1 root root 1286144 okt 19  2013 idmap.ldb
-rw-r--r-- 1 root root      92 okt 19  2013 krb5.conf
srwxrwxrwx 1 root root       0 mei 19 21:46 ldapi
drwxr-x--- 2 root root    4096 mei 19 21:46 ldap_priv
-r--r--r-- 1 root root     220 okt 19  2013 named.conf.update
-rw------- 1 root root 1286144 okt 19  2013 privilege.ldb
-rw------- 1 root root     696 okt 19  2013 randseed.tdb
-rw------- 1 root root 4251648 okt 19  2013 sam.ldb
drwx------ 2 root root    4096 okt 19  2013 sam.ldb.d
-rw------- 1 root root     696 mei 19 21:46 schannel_store.tdb
-rw------- 1 root root    1057 okt 19  2013 secrets.keytab
-rw------- 1 root root 1286144 okt 19  2013 secrets.ldb
-rw------- 1 root root  430080 okt 19  2013 secrets.tdb
-rw------- 1 root root 1286144 okt 19  2013 share.ldb
drwxr-xr-x 3 root root    4096 okt 19  2013 smbd.tmp
-rw-r--r-- 1 root root     955 okt 19  2013 spn_update_list
drwxr-xr-x 2 root root    4096 okt 19  2013 tls
dpkg: error processing archive /var/cache/apt/archives/samba-libs_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/samba-libs_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dannyboy79 on 2014-05-24
did you even bother reading the bug report that's clearly linked within the error message? basically you need to delete /var/lib/samba/private/secrets.tdb. BUT if you're unsure if that will have bad consequences than just move it to your desktop for now. Once you move the file the upgrade should work just fine. It's all explained at the bug here: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=726472](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=726472)

---

