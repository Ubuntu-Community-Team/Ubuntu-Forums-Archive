---
title: "Serious problems under upgrade"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by niels on 2005-10-14
Hi, I have just tryed to upgrade from hoary to breezy, but the process stopped becaus of some problems. I have put an dump from the install process here (some of it is in danish, but I hope you'll understand):
> 
Hentede 713MB på 6h57m7s (28,5kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
(Læser database... 80259 filer og mapper aktuelt installeret.)
Gør klar til at erstatte linux-kernel-headers 2.5.999-test7-bk-17 (med ..../linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb)...
Udpakker erstatning linux-kernel-headers...
Gør klar til at erstatte libc6-dev 2.3.2.ds1-20ubuntu14 (med ..../libc6-dev_2.3.5-1ubuntu12_i386.deb)...
Udpakker erstatning libc6-dev...
Gør klar til at erstatte locales 2.3.2.ds1-20ubuntu14 (med ..../locales_2.3.5-1ubuntu12_all.deb)...
Udpakker erstatning locales...
Gør klar til at erstatte libc6 2.3.2.ds1-20ubuntu14 (med ..../libc6_2.3.5-1ubuntu12_i386.deb)...
Udpakker erstatning libc6...
Setting up libc6 (2.3.5-1ubuntu12) ...
Checking for services that may need to be restarted...done.

Name Service Switch has changed in the C Library: post-installation question.
Running programs may not be able to do NSS lookups until they are
restarted (for services such as ssh, this can affect your ability to
login).
Note: restarting sshd/telnetd should not affect any existing connections.

The services detected are: inetd rsync apache2 cupsys postfix cron

If other services begin to fail mysteriously after this upgrade,
it may be necessary to restart them too.  We strongly recommend
you to reboot your machine to avoid the NSS related trouble.

Do you wish to Restart Services? [Y/n] y

Restarting services possibly affected by the upgrade:
   inetd: stopping...starting...done.
   rsync: stopping...starting...done.
   apache2: stopping...starting...done.
   cupsys: stopping...starting...done.
   postfix: stopping...starting...done.
   cron: stopping...starting...done.

Services restarted successfully.

Current default timezone: 'Europe/Copenhagen'.
Local time is now:      Fri Oct 14 08:02:07 CEST 2005.
Universal Time is now:  Fri Oct 14 06:02:07 UTC 2005.
Run 'tzconfig' if you wish to change it.

Hentede 713MB på 6h57m7s (28,5kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
(Læser database... 80259 filer og mapper aktuelt installeret.)
Gør klar til at erstatte linux-kernel-headers 2.5.999-test7-bk-17 (med ..../linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb)...
Udpakker erstatning linux-kernel-headers...
Gør klar til at erstatte libc6-dev 2.3.2.ds1-20ubuntu14 (med ..../libc6-dev_2.3.5-1ubuntu12_i386.deb)...
Udpakker erstatning libc6-dev...
Gør klar til at erstatte locales 2.3.2.ds1-20ubuntu14 (med ..../locales_2.3.5-1ubuntu12_all.deb)...
Udpakker erstatning locales...
Gør klar til at erstatte libc6 2.3.2.ds1-20ubuntu14 (med ..../libc6_2.3.5-1ubuntu12_i386.deb)...
Udpakker erstatning libc6...
Setting up libc6 (2.3.5-1ubuntu12) ...
Checking for services that may need to be restarted...done.

Name Service Switch has changed in the C Library: post-installation question.
Running programs may not be able to do NSS lookups until they are
restarted (for services such as ssh, this can affect your ability to
login).
Note: restarting sshd/telnetd should not affect any existing connections.

The services detected are: inetd rsync apache2 cupsys postfix cron

If other services begin to fail mysteriously after this upgrade,
it may be necessary to restart them too.  We strongly recommend
you to reboot your machine to avoid the NSS related trouble.

Do you wish to Restart Services? [Y/n] y

Restarting services possibly affected by the upgrade:
   inetd: stopping...starting...done.
   rsync: stopping...starting...done.
   apache2: stopping...starting...done.
   cupsys: stopping...starting...done.
   postfix: stopping...starting...done.
   cron: stopping...starting...done.

Services restarted successfully.

Current default timezone: 'Europe/Copenhagen'.
Local time is now:      Fri Oct 14 08:02:07 CEST 2005.
Universal Time is now:  Fri Oct 14 06:02:07 UTC 2005.
Run 'tzconfig' if you wish to change it.

(Reading database ... 80340 files and directories currently installed.)
Preparing to replace libc6-i686 2.3.2.ds1-20ubuntu14 (using ..../libc6-i686_2.3.5-1ubuntu12_i386.deb) ...
Unpacking replacement libc6-i686 ...
dpkg: error processing /var/cache/apt/archives/liburi-perl_1.35-1_all.deb (--unpack):
  cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/libhtml-parser-perl_3.45-2_i386.deb (--unpack):
  cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/libwww-perl_5.803-4_all.deb (--unpack):
  cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/perl-modules_5.8.7-5ubuntu1_all.deb (--unpack):
  cannot access archive: No such file or directory
Preparing to replace libdb4.2 4.2.52-17ubuntu1 (using ..../libdb4.2_4.2.52-19ubuntu4_i386.deb) ...
Unpacking replacement libdb4.2 ...
dpkg: error processing /var/cache/apt/archives/perl_5.8.7-5ubuntu1_i386.deb (--unpack):
  cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/libperl5.8_5.8.7-5ubuntu1_i386.deb (--unpack):
  cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/perl-base_5.8.7-5ubuntu1_i386.deb (--unpack):
  cannot access archive: No such file or directory
Errors were encountered while processing:
  /var/cache/apt/archives/liburi-perl_1.35-1_all.deb
  /var/cache/apt/archives/libhtml-parser-perl_3.45-2_i386.deb
  /var/cache/apt/archives/libwww-perl_5.803-4_all.deb
  /var/cache/apt/archives/perl-modules_5.8.7-5ubuntu1_all.deb
  /var/cache/apt/archives/perl_5.8.7-5ubuntu1_i386.deb
  /var/cache/apt/archives/libperl5.8_5.8.7-5ubuntu1_i386.deb
  /var/cache/apt/archives/perl-base_5.8.7-5ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
niels@nielslaptop:~$


Wat do I do?

Niels

---

### Post by daller on 2005-12-01
Is this still a problem?

---

### Post by Topsiho on 2005-12-01
My experiences with upgrading (to be honest this was with other distributions like Mandrake (now it's called Mandriva)) is that it is always wiser to do a fresh install, without reformatting your /home directory. Therefore the /home directory should sit in it's own partition.

Though I never lost my personal files in /home this way I of course urge anyone doing an upgrade or fresh install to back up his valuable personal files first. But that goes without saying :) and is only to be sure. And: those files should already be backed up anyway ....

Topsiho

---

### Post by bwog on 2005-12-01
A dist-upgrade to breezy doesnt have to give problems, there is no need to reinstall unless there are very serious isseus after the upgrade.

---

### Post by Topsiho on 2005-12-01
OK, if that's so than Ubuntu really is better than Mandrake was :)

I don't know about Mandriva as I left Mandrake when it started being a commercial distribution (very expensive too compared to Windows, considering a long term membership of the Mandrake club).

(FYI I contribute to the Linux community too by translating applications for KDE, and file an occasional bug report)

Topsiho

---

