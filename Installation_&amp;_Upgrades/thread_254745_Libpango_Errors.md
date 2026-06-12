---
title: "Libpango Errors"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by iphands on 2006-09-10
after a recent update and upgrade I get 

```

root@kids:/home/kids# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libpango1.0-common
Suggested packages:
  ttf-thryomanes
The following packages will be upgraded:
  libpango1.0-common
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
3 not fully installed or removed.
Need to get 0B/32.4kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 125546 files and directories currently installed.)
Preparing to replace libpango1.0-common 1.12.3-0ubuntu1 (using .../libpango1.0-common_1.12.3-0ubuntu3_i386.deb) ...
Unpacking replacement libpango1.0-common ...
dpkg: error processing /var/cache/apt/archives/libpango1.0-common_1.12.3-0ubuntu3_i386.deb (--unpack):
 unable to create `./usr/sbin/update-pango-modules': Permission denied
Errors were encountered while processing:
 /var/cache/apt/archives/libpango1.0-common_1.12.3-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So I decided to try and rename this update-pango-modules

```

root@kids:/usr/sbin# mv update-pango-modules update-pango-modules.bak
mv: cannot move `update-pango-modules' to `update-pango-modules.bak': Permission denied
```

So then (getting desperate) I tried to remove the file!! w/ -f

```

root@kids:/usr/sbin# rm -f update-pango-modules
rm: cannot remove `update-pango-modules': Permission denied
```

WTF???????
I'm stumped.....

---

### Post by iphands on 2006-09-12
still happening... anyone know why i can't mv or rm anything in /usr/sbin?? even as root??

---

### Post by iphands on 2006-09-14
bumpity bump bump

---

### Post by hangfire on 2006-09-17
Usually when root gets a perm denied on file operations, it's a read-only file system, or mounted with root quash, such as NFS or maybe a loopback filesystem.

---

### Post by evil_cat on 2008-05-10
Download the libpango-common from
[http://packages.ubuntu.com/gutsy-updates/libpango1.0-common](http://packages.ubuntu.com/gutsy-updates/libpango1.0-common)

Then download libpango1.0-0 from
[http://packages.ubuntu.com/gutsy-updates/libpango1.0-0](http://packages.ubuntu.com/gutsy-updates/libpango1.0-0)

This will install the latest libpango (1.18.3-0ubuntu)

---

