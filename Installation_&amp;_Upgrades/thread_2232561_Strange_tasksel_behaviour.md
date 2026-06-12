---
title: "Strange tasksel behaviour"
date: 2014-07-02
forum: Installation &amp; Upgrades
---

### Post by Scorry on 2014-07-02
Good day.

Long and magic history in two repetitive parts.
Initial point: fresh install of Ubuntu server 14.04 amd64 on clear, formatted partitions. Installation media crc-checked. Tasksel from start charged with openssh, lamp, samba and mail. All is good, all is working. But the desire to radically change something appears sometimes.
Well, OK:
```
apt-get purge lamp-server^
```
And response was:
```
The following packages will be REMOVED
  apache2* apache2-bin* apache2-data* apache2-mpm-prefork* libaio1*
  libapache2-mod-php5* libapr1* libaprutil1* libaprutil1-dbd-sqlite3*
  libaprutil1-ldap* libdbd-mysql-perl* libdbi-perl* libhtml-template-perl*
  libmailutils4* libmysqlclient18* libterm-readkey-perl* libwrap0* mailutils*
  mysql-client-5.5* mysql-client-core-5.5* mysql-common* mysql-server*
  mysql-server-5.5* mysql-server-core-5.5* openssh-server* php5-cli*
  php5-common* php5-json* php5-mysql* php5-readline* postfix*
  samba-vfs-modules* ssl-cert* tcpd*
```
Postfix and samba deleted too in some strange reasons.

And if I prefer to purge mail-server: bazaar, samba and openssh is under the strike:
```
apt-get purge mail-server^
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'libpython2.7-stdlib' for task 'mail-server'
Note, selecting 'bsd-mailx' for task 'mail-server'
Note, selecting 'postfix' for task 'mail-server'
Note, selecting 'python-minimal' for task 'mail-server'
Note, selecting 'libassuan0' for task 'mail-server'
Note, selecting 'libtokyocabinet9' for task 'mail-server'
Note, selecting 'mutt' for task 'mail-server'
Note, selecting 'procmail' for task 'mail-server'
Note, selecting 'python2.7' for task 'mail-server'
Note, selecting 'ssl-cert' for task 'mail-server'
Note, selecting 'dovecot-core' for task 'mail-server'
Note, selecting 'dovecot-pop3d' for task 'mail-server'
Note, selecting 'python' for task 'mail-server'
Note, selecting 'libpython-stdlib' for task 'mail-server'
Note, selecting 'python2.7-minimal' for task 'mail-server'
Note, selecting 'dovecot-imapd' for task 'mail-server'
Note, selecting 'libwrap0' for task 'mail-server'
Note, selecting 'libpython2.7-minimal' for task 'mail-server'
Note, selecting 'tcpd' for task 'mail-server'
Note, selecting 'libgpgme11' for task 'mail-server'
Package 'bsd-mailx' is not installed, so not removed
Package 'libtokyocabinet9' is not installed, so not removed
Package 'mutt' is not installed, so not removed
Package 'procmail' is not installed, so not removed
Package 'dovecot-core' is not installed, so not removed
Package 'dovecot-imapd' is not installed, so not removed
Package 'dovecot-pop3d' is not installed, so not removed
The following packages will be REMOVED
  bzr* libassuan0* libgpgme11* libmailutils4* libpam-smbpass*
  libpython-stdlib* libpython2.7* libpython2.7-minimal* libpython2.7-stdlib*
  libsmbclient* libwrap0* mailutils* mysql-server* mysql-server-5.5*
  mysql-server-core-5.5* openssh-server* postfix* python* python-bzrlib*
  python-chardet* python-configobj* python-crypto* python-dbus*
  python-dnspython* python-gi* python-gpgme* python-httplib2* python-keyring*
  python-launchpadlib* python-lazr.restfulclient* python-lazr.uri* python-ldb*
  python-minimal* python-ntdb* python-oauth* python-paramiko*
  python-pkg-resources* python-requests* python-samba* python-secretstorage*
  python-simplejson* python-six* python-talloc* python-tdb* python-urllib3*
  python-wadllib* python-zope.interface* python2.7* python2.7-minimal* samba*
  samba-common-bin* samba-dsdb-modules* samba-libs* samba-vfs-modules*

```

Server after that magic was reinstalled, media was crc-checked &#8212; and second install has exactly same trouble with tasksel tasks.

What the root of problem?
Any ideas?

I'm nearly insane with this strange magic :-(

---

### Post by mastablasta on 2014-07-03
dependencies are also removed. what seems to be the problem?

---

### Post by tgalati4 on 2014-07-03
*tasksel* uses metapackages--dummy packages that are placeholders for a list of packages.  This is helpful for installing a service such as a LAMP stack, which contains several dozen packages which are required to run an Apache web server.  Mail is installed because web servers will send mail when problems arise.  SAMBA is used for file sharing.  Not clear why it is a dependency for mail--other than being able to access SAMBA shares for storing mail.

In general, if you install with metapackages, then you need to be careful removing single packages because that will break the service that was installed with the metapackage.  Tasksel (and running servers in general) is for advanced users so there is an assumption that one knows what is going on.

When setting up a server, you normally repress the desire to change things radically.

---

