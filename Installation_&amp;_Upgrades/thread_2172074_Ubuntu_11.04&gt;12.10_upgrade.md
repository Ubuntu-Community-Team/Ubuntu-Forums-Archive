---
title: "Ubuntu 11.04&gt;12.10 upgrade"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by liviusbr on 2013-09-03
Hi All,

I am trying to make a dist upgrade by command line and I am getting the following error :

```
root@SPB-MMH:/usr/bin# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.0.0-32 linux-headers-3.0.0-32-server
The following packages will be upgraded:
  accountsservice apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common apparmor apport apt apt-transport-https apt-utils bind9-host bzip2 command-not-found command-not-found-data dbus dnsutils dpkg gnupg gpgv grub-common
  gzip ifupdown initramfs-tools initramfs-tools-bin initscripts insserv isc-dhcp-client isc-dhcp-common iso-codes landscape-common language-pack-en language-pack-en-base language-selector-common libaccountsservice0 libapt-inst1.3
  libapt-pkg4.11 libbind9-60 libbz2-1.0 libcurl3-gnutls libdbus-1-3 libdbus-glib-1-2 libdns69 libfreetype6 libgc1c2 libisc62 libisccc60 libisccfg62 libjs-jquery liblwres60 libncurses5 libncursesw5 libpam-modules libpam-modules-bin
  libpam-runtime libpam0g libpng12-0 libpython2.7 libtinfo5 libudev0 libxml2 linux-firmware linux-headers-server mawk multiarch-support ncurses-base ncurses-bin openssl perl perl-base python-apport python-crypto python-gobject
  python-gobject-cairo python-httplib2 python-keyring python-launchpadlib python-pam python-pkg-resources python-problem-report python2.7 python2.7-minimal sudo sysv-rc sysvinit-utils tzdata ubuntu-minimal ubuntu-standard udev
  update-manager-core upstart vim vim-common vim-runtime vim-tiny
94 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0 B/79.0 MB of archives.
After this operation, 102 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 47222 files and directories currently installed.)
Preparing to replace apache2-mpm-worker 2.2.20-1ubuntu1.3 (using .../apache2-mpm-worker_2.2.20-1ubuntu1.4_amd64.deb) ...
Unpacking replacement apache2-mpm-worker ...
dpkg: error processing /var/cache/apt/archives/apache2-mpm-worker_2.2.20-1ubuntu1.4_amd64.deb (--unpack):
 error creating symbolic link `./usr/sbin/apache2': Permission denied
Preparing to replace apache2.2-common 2.2.20-1ubuntu1.3 (using .../apache2.2-common_2.2.20-1ubuntu1.4_amd64.deb) ...
Unpacking replacement apache2.2-common ...
dpkg: error processing /var/cache/apt/archives/apache2.2-common_2.2.20-1ubuntu1.4_amd64.deb (--unpack):
 unable to create `/usr/sbin/a2enmod.dpkg-new' (while processing `./usr/sbin/a2enmod'): Permission denied
Preparing to replace apache2.2-bin 2.2.20-1ubuntu1.3 (using .../apache2.2-bin_2.2.20-1ubuntu1.4_amd64.deb) ...
Unpacking replacement apache2.2-bin ...
dpkg: error processing /var/cache/apt/archives/apache2.2-bin_2.2.20-1ubuntu1.4_amd64.deb (--unpack):
 unable to create `/usr/sbin/httxt2dbm.dpkg-new' (while processing `./usr/sbin/httxt2dbm'): Permission denied
Preparing to replace apache2-utils 2.2.20-1ubuntu1.2 (using .../apache2-utils_2.2.20-1ubuntu1.4_amd64.deb) ...
Unpacking replacement apache2-utils ...
dpkg: error processing /var/cache/apt/archives/apache2-utils_2.2.20-1ubuntu1.4_amd64.deb (--unpack):
 unable to create `/usr/sbin/rotatelogs.dpkg-new' (while processing `./usr/sbin/rotatelogs'): Permission denied
No apport report written because MaxReports is reached already
                                                              Preparing to replace perl 5.12.4-4 (using .../perl_5.12.4-4ubuntu0.2_amd64.deb) ...
Unpacking replacement perl ...
dpkg: error processing /var/cache/apt/archives/perl_5.12.4-4ubuntu0.2_amd64.deb (--unpack):
 unable to create `/usr/bin/cpanp.dpkg-new' (while processing `./usr/bin/cpanp'): Permission denied
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace perl-base 5.12.4-4 (using .../perl-base_5.12.4-4ubuntu0.2_amd64.deb) ...
Unpacking replacement perl-base ...
dpkg: error processing /var/cache/apt/archives/perl-base_5.12.4-4ubuntu0.2_amd64.deb (--unpack):
 unable to create `/usr/bin/perl.dpkg-new' (while processing `./usr/bin/perl'): Permission denied
No apport report written because MaxReports is reached already
                                                              Processing triggers for ufw ...
WARN: /etc is group writable!
WARN: /usr is world writable!
WARN: /usr is group writable!
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/apache2-mpm-worker_2.2.20-1ubuntu1.4_amd64.deb
 /var/cache/apt/archives/apache2.2-common_2.2.20-1ubuntu1.4_amd64.deb
 /var/cache/apt/archives/apache2.2-bin_2.2.20-1ubuntu1.4_amd64.deb
 /var/cache/apt/archives/apache2-utils_2.2.20-1ubuntu1.4_amd64.deb
 /var/cache/apt/archives/perl_5.12.4-4ubuntu0.2_amd64.deb
 /var/cache/apt/archives/perl-base_5.12.4-4ubuntu0.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



Any idea ?

---

### Post by maestrobwh1 on 2013-09-03
Do you mean 12.04 to 12.10?  If not

first you need to upgrade to 11.10, ocelot, then to 12.04 precise, then to 12.10 quantal.  The only time you can jump releases is LTS to LTS, like 10.04 to 12.04

As per: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You need to change /etc/apt/sources.list to

## EOL upgrade sources.list

```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) oneiric-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
```

make sure you disable all your other repos (I'd use synaptic but there are other ways of doing this)

then do 

```
sudo apt-get clean && sudo apt-get update && sudo apt-get -yd dist-upgrade
```

You can take the -y flag out and make sure you want to confirm the procedure.  This will purge /car/casche/apt/archives, and download the new packages there

Reboot into recovery mode (running this from the desktop can be dicey, because if X crashes during the upgrade, the process will stop mid way and you might not be able to fix it), 

make sure you are in read-write mode

```
mount -o remount,rw /
mount -a
apt-get -y dist upgrade
```

Then, after that completes, and hopefully goes well (it will want to remove packages), you need to *reboot normally* and replace the /etc/apt/sources.list contents with:

```
###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
```

then

```
sudo apt-get clean && sudo apt-get update && sudo apt-get -yd dist-upgrade
```

What this does is download the packages for the next upgrade, but not install them

Then I would reboot into recovery mode again, drop to a root shell, make sure you are in read-write mode as before:

```
mount -o remount,rw /
mount -a
apt-get -y dist upgrade
```

This will get you to 12.04.3  Personally, I'd stay there, but then you can perform a regular upgrade through normal means.  I have 13.04 and 12.04 on different machines.  13.04 has the ability to tweak unity, but I am not convinced that the aggravation of having to upgrade (non LTS releases are not supported very long now) again soon. 12.04 and 12.10 and 13.04 are near identical in user utility and appearance.

---

### Post by liviusbr on 2013-09-04
Sorry, I meant 11.10 to 12.04 upgrade.. I am already in 11.10..

---

### Post by grahammechanical on 2013-09-04
The command apt-get dist-upgrade does not upgrade one version of Ubuntu to the next version. It upgrades the existing version.

note what the wiki says

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

```
sudo apt-get upgrade
```

> [COLOR=#333333][FONT=Ubuntu]This command upgrades all installed packages. This is the equivalent of "Mark all upgrades" in Synaptic.[/FONT][/COLOR]

```
sudo apt-get dist-upgrade
```

> [COLOR=#333333][FONT=Ubuntu]The same as the above, except add the "smart upgrade" checkbox. It tells APT to use "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary.[/FONT][/COLOR]

This is how to upgrade fron 11.10 to 12.04

[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

The command line way is

```
sudo apt-get do-release-upgrade
```

[https://help.ubuntu.com/lts/serverguide/installing-upgrading.html](https://help.ubuntu.com/lts/serverguide/installing-upgrading.html)

That is for server installations.

Regards.

---

### Post by liviusbr on 2013-09-04
Hi,

I did what the wiki says, actually!

sudo apt-get upgrade, then


sudo apt-get dist-upgrade

What I've pasted initially are the results of the second command. Anyone encountered something similar?

Thanks,
Liviu

---

