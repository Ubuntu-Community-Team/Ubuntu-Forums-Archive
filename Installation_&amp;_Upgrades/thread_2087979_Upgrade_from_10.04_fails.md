---
title: "Upgrade from 10.04 fails"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by henfri on 2012-11-25
Hello,

I think, I have a problem:
```
A fatal error occurred

Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.

SystemError: E:Internal Error, No file name for libc6



Could not install the upgrades

The upgrade has aborted. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).

Please report this bug in a browser at
http://bugs.launchpad.net/ubuntu/+source/update-manager/+filebug and
attach the files in /var/log/dist-upgrade/ to the bug report.
installArchives() failed

dpkg: dependency problems prevent configuration of libc6:i386:
 libc6:i386 depends on tzdata.
dpkg: error processing libc6:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgcc1:i386:
 libgcc1:i386 depends on libc6 (>= 2.2.4); however:
  Package libc6:i386 is not configured yet.
dpkg: error processing libgcc1:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6:i386
 libgcc1:i386

Upgrade complete

The upgrade has completed but there were errors during the upgrade
process.

```I have no clue how to fix this :-(

Is it realistic to fix this, or should I rather install a fresh 12.04?

Greetings,
Hendrik

---

### Post by raja.genupula on 2012-11-25
try this in your terminal 
```
sudo -i
dpkg -r  libc6:i386
 dpkg -r libgcc1:i386
sudo apt-get update
sudo apt-get install -f
```

then try again

---

### Post by henfri on 2012-11-25
Hi Raja,

thanks for your hint. I tried it immediatly. Your commands ran sucessfully, but the result was the same:
```
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg'
extracting 'precise.tar.gz'

Could not install the upgrades

The upgrade has aborted. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).

Please report this bug in a browser at
http://bugs.launchpad.net/ubuntu/+source/update-manager/+filebug and
attach the files in /var/log/dist-upgrade/ to the bug report.
installArchives() failed

Setting up libxml-sax-base-perl (1.07-1) ...
Setting up libxml-sax-perl (0.99+dfsg-1ubuntu0.1) ...
update-perl-sax-parsers: Registering Perl SAX parser XML::SAX::PurePerl with priority 10...
update-perl-sax-parsers: Updating overall Perl SAX parser modules info file...
Setting up libudev0 (175-0ubuntu9.1) ...
dpkg: dependency problems prevent configuration of libc6:i386:
 libc6:i386 depends on tzdata.
dpkg: error processing libc6:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgcc1:i386:
 libgcc1:i386 depends on libc6 (>= 2.2.4); however:
  Package libc6:i386 is not configured yet.
dpkg: error processing libgcc1:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtinfo5:i386:
 libtinfo5:i386 depends on libc6 (>= 2.4); however:
  Package libc6:i386 is not configured yet.
dpkg: error processing libtinfo5:i386 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libc6:i386
 libgcc1:i386
 libtinfo5:i386

Upgrade complete

The upgrade has completed but there were errors during the upgrade
process.

To continue please press [ENTER]

```

:-(

Greetings,
Hendrik

---

### Post by henfri on 2012-11-25
Hello,

is this maybe the root cause?
```
2012-11-25 12:10:27,003 DEBUG plugins for condition 'StartUpgrade' are '[]'
2012-11-25 12:10:27,004 DEBUG plugins for condition 'preciseStartUpgrade' are '[]'
2012-11-25 12:10:27,004 DEBUG plugins for condition 'from_lucidStartUpgrade' are '[]'
2012-11-25 12:10:27,004 DEBUG quirks: running StartUpgrade
2012-11-25 12:10:27,004 DEBUG check if patch '_usr_bin_pycompile.b17cebfbf18d152702278b15710d5095.97c07a02e5951cf68cb3f86534f6f917' needs to be applied
2012-11-25 12:10:27,004 DEBUG target for '_usr_bin_pycompile.b17cebfbf18d152702278b15710d5095.97c07a02e5951cf68cb3f86534f6f917' is '_usr_bin_pycompile' -> '/usr/bin/pycompile'
2012-11-25 12:10:27,128 WARNING unexpected target md5sum, skipping: '/usr/bin/pycompile'
```

Greetings,
Hendrik

---

### Post by henfri on 2012-11-25
I think, it is this bug, isn't it?
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1017001](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1017001)
Unfortunately, I could not find  a solution posted in this bug or the linked ones.

Greetings,
Hendrik

---

### Post by henfri on 2012-11-25
Hello,

I'm installing 12.04 from scratch now.

Thanks,
Hendrik

---

