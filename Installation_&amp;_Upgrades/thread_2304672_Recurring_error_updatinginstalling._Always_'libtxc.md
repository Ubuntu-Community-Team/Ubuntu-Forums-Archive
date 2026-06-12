---
title: "Recurring error updating/installing. Always 'libtxc-dxtn-s2tc0:amd64' missing..."
date: 2015-11-28
forum: Installation &amp; Upgrades
---

### Post by slowjoe2 on 2015-11-28
Recurring error during every software install, removal or upgrade.  See apt-get upgrade output below. (Possibly a corrupt file? System seems unstable lately, i.e., intermittent trouble booting and occasional crash.) Recently upgraded from the Pangolin LTS to the Tahr LTS. Thanks for any help!

```
joe@Frank:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apport apport-gtk dpkg grub-common grub-pc grub-pc-bin grub2-common
  icedtea-netx icedtea-netx-common im-config krb5-locales libdpkg-perl libffi6
  libffi6:i386 libgssapi-krb5-2 libgssapi-krb5-2:i386 libido3-0.1-0
  libk5crypto3 libk5crypto3:i386 libkrb5-3 libkrb5-3:i386 libkrb5support0
  libkrb5support0:i386 libmbim-glib0 libmm-glib0 libnautilus-extension1a
  libpng12-0 libpng12-0:i386 libpoppler-glib8 libpoppler-qt4-4 libpoppler44
  libwhoopsie0 libxml2 libxml2:i386 libxml2-utils linux-firmware modemmanager
  nautilus-data openjdk-7-jre openjdk-7-jre-headless poppler-utils
  python-apport python-libxml2 python-problem-report python3-apport
  python3-problem-report whoopsie
47 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/75.4 MB of archives.
After this operation, 446 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libtxc-dxtn-s2tc0:amd64' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by ian-weisser on 2015-11-28
> **slowjoe2 said:**
> dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libtxc-dxtn-s2tc0:amd64' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)


The first thing I would try is to reinstall a fresh copy that isn't missing anything.
```
sudo apt-get clean libtxc-dxtn-s2tc0                  ## Delete the old copy stored in cache
sudo apt-get install --reinstall libtxc-dxtn-s2tc0    ## Download and reinstall a fresh copy
```

---

### Post by slowjoe2 on 2015-11-28
Thanks.  Unfortunately I get the same message, see below:

> joe@Frank:~$ sudo apt-get clean libtxc-dxtn-s2tc0
[sudo] password for joe: 
joe@Frank:~$ sudo apt-get install --reinstall libtxc-dxtn-s2tc0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 2 to reinstall, 0 to remove and 47 not to upgrade.
Need to get 99.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/main libtxc-dxtn-s2tc0 amd64 0~git20131104-1.1 [51.8 kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/main libtxc-dxtn-s2tc0 i386 0~git20131104-1.1 [48.1 kB]
Fetched 99.9 kB in 0s (274 kB/s)                 
Selecting previously unselected package libtxc-dxtn-s2tc0:amd64.
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libtxc-dxtn-s2tc0:amd64' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

I believe I have both libtxc-dxtn-s2tc0:amd64 and libtxc-dxtn-s2tc0:i386.  My research suggests there might be a conflict as a result of the upgrade, but nothing specific to this particular file.  The actual file libtxc-dxtn-s2tc0:amd64.list has a file type of unknown, opens in leafpad but is empty.

---

### Post by slowjoe2 on 2015-11-29
OK, I'm pretty sure that the file mentioned is corrupt.  Even when I try to delete it, or the package that contains it, I get this message:

> (synaptic:7070): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libtxc-dxtn-s2tc0:amd64' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

Until it's resolved I can't install, remove, or otherwise update my system.  I would so appreciate some help.
Have already tried: sudo rm libtxc-dxtn-s2tc0 -f

---

### Post by ian-weisser on 2015-11-29
> **slowjoe2 said:**
> The actual file **libtxc-dxtn-s2tc0:amd64.list** has a file type of unknown, opens in leafpad but is empty.

What's the full path of that file?

If you are talking about /var/lib/dpkg/info/libtxc-dxtn-s2tc0:amd64.list , here is what it mine contains:
```
/.
/usr
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libtxc_dxtn_s2tc.so.0.0.0
/usr/share
/usr/share/doc
/usr/share/doc/libtxc-dxtn-s2tc0
/usr/share/doc/libtxc-dxtn-s2tc0/copyright
/usr/share/doc/libtxc-dxtn-s2tc0/changelog.Debian.gz
/usr/share/doc/libtxc-dxtn-s2tc0/README.txt
/usr/lib/x86_64-linux-gnu/libtxc_dxtn_s2tc.so.0

```

---

### Post by slowjoe2 on 2015-11-30
I deleted the file using command line then created a new blank one.  I was then able to successfully upgrade and installed software using 'software updater'.

I also reinstalled both libtxc-dxtn-s2tc0 and libtxc-dxtn-s2tc0:i386 using synaptic.  The blank file I'd created was then populated with exactly the data you listed above.

(This must all prove the file became corrupted during a crash.  I'm not sure why my system is unstable though.  It seems really intermittent - can't pick up any patterns)

Thanks for your helpful direction ian-weisser.  I learned a lot although it was all fairly simple in the end.  A happy festive season to you. :KS

---

