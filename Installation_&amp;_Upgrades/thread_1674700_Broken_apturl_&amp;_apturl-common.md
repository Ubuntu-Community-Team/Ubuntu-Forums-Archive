---
title: "Broken apturl &amp; apturl-common"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by dj_fle on 2011-01-24
Hello, all!

I upgraded from 10.04 to 10.10, resulting in broken apturl / apturl-common.

The graphical Update Manager outputs the following:

```
The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details: apturl
```

When I run the suggestion,

```

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apturl-common
The following packages will be upgraded:
  apturl-common
1 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
2 not fully installed or removed.
Need to get 0B/15.8kB of archives.
After this operation, 24.6kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `libfaad2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libprotoc5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86vm1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiw30' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-khmeros-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xml-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireless-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-django-tagging' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkate1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libndesk-dbus-glib1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86misc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apturl-common' missing, assuming package has no files currently installed.
(Reading database ... 275367 files and directories currently installed.)
Preparing to replace apturl-common 0.4.1ubuntu4 (using .../apturl-common_0.4.1ubuntu7_amd64.deb) ...
pycentral: pycentral pkgremove: package apturl-common is not installed
pycentral pkgremove: package apturl-common is not installed
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package apturl-common is not installed
pycentral pkgremove: package apturl-common is not installed
dpkg: error processing /var/cache/apt/archives/apturl-common_0.4.1ubuntu7_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package apturl-common is not installed
pycentral pkginstall: package apturl-common is not installed
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apturl-common_0.4.1ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Would a solution be to reinstall apturl from source? How would I go about doing that?


Many thanks.

---

### Post by sikander3786 on 2011-01-24
Welcome to the forums :-)

Try using an older dpkg/status file.

Applications > Accessories > Terminal:

Do these commands one by one.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

Please post the errors if they persist.

---

### Post by dj_fle on 2011-01-24
All went well up to:

```

$ sudo dpkg --configure -a

Setting up python-apt (0.7.96.1ubuntu11.1) ...
Processing triggers for python-central ...
dpkg: error processing apturl-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 apturl-common

```

Thank you for your reply!

---

### Post by sikander3786 on 2011-01-24
Try,

```
sudo apt-get install --reinstall apturl-common
```

---

### Post by dj_fle on 2011-01-24
It's a tough one!! :evil:

```

$ sudo apt-get install --reinstall apturl-common

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apturl-common
1 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
1 not fully installed or removed.
Need to get 0B/15.8kB of archives.
After this operation, 24.6kB disk space will be freed.
(Reading database ... 
dpkg: warning: files list file for package `libfaad2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libprotoc5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86vm1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiw30' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-khmeros-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xml-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireless-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-django-tagging' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkate1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libndesk-dbus-glib1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86misc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apturl-common' missing, assuming package has no files currently installed.
(Reading database ... 275354 files and directories currently installed.)
Preparing to replace apturl-common 0.4.1ubuntu4 (using .../apturl-common_0.4.1ubuntu7_amd64.deb) ...
pycentral: pycentral pkgremove: package apturl-common is not installed
pycentral pkgremove: package apturl-common is not installed
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package apturl-common is not installed
pycentral pkgremove: package apturl-common is not installed
dpkg: error processing /var/cache/apt/archives/apturl-common_0.4.1ubuntu7_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package apturl-common is not installed
pycentral pkginstall: package apturl-common is not installed
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apturl-common_0.4.1ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by sikander3786 on 2011-01-24
Try removing the package from /archives manually and then do a re-install.

```
sudo apt-get remove --purge apturl-common
```

```
sudo rm /var/cache/apt/archives/apturl-common_0.4.1ubuntu7_amd64.deb
```

```
sudo apt-get install apturl-common
```

---

### Post by dj_fle on 2011-01-24
...

```

$ sudo apt-get remove --purge apturl-common

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apturl-common*
0 upgraded, 0 newly installed, 1 to remove and 32 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing apturl-common (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 apturl-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by sikander3786 on 2011-01-24
Ok. Try these.

```
sudo rm /var/cache/apt/archives/apturl-common_0.4.1ubuntu7_amd64.deb
```

```
sudo apt-get install --reinstall apturl-common
```

---

### Post by dj_fle on 2011-01-24
Did we hit a deadlock?

```

$ sudo apt-get install --reinstall apturl-common

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apturl-common
1 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
1 not fully installed or removed.
Need to get 15.8kB of archives.
After this operation, 24.6kB disk space will be freed.
Get:1 http://mx.archive.ubuntu.com/ubuntu/ maverick/main apturl-common amd64 0.4.1ubuntu7 [15.8kB]
Fetched 15.8kB in 1s (8241B/s)         
Selecting previously deselected package apturl-common.
(Reading database ... 
dpkg: warning: files list file for package `libfaad2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libprotoc5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86vm1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiw30' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-khmeros-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xml-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireless-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-django-tagging' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkate1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libndesk-dbus-glib1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86misc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apturl-common' missing, assuming package has no files currently installed.
(Reading database ... 275354 files and directories currently installed.)
Preparing to replace apturl-common 0.4.1ubuntu4 (using .../apturl-common_0.4.1ubuntu7_amd64.deb) ...
pycentral: pycentral pkgremove: package apturl-common is not installed
pycentral pkgremove: package apturl-common is not installed
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package apturl-common is not installed
pycentral pkgremove: package apturl-common is not installed
dpkg: error processing /var/cache/apt/archives/apturl-common_0.4.1ubuntu7_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package apturl-common is not installed
pycentral pkginstall: package apturl-common is not installed
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apturl-common_0.4.1ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by sikander3786 on 2011-01-24
Not a dead lock. I believe it is curable but packages in a bad state are hard to deal with. Need to try everything from the book ;-)

```
sudo apt-get remove --purge --force apturl-common
```

Or,

```
sudo rm /var/lib/dpkg/info/apturl-common
```

```
sudo dpkg --remove --force-remove-reinstreq apturl-common
```

---

### Post by dj_fle on 2011-01-24
Finally!! Thank you so much!!

For the sake of completeness:

```

$ sudo apt-get remove --purge --force apturl-common
E: Command line option --force is not understood

```

```

$ sudo rm /var/lib/dpkg/info/apturl-common
rm: cannot remove `/var/lib/dpkg/info/apturl-common': No such file or directory

```

```

$ sudo rm /var/lib/dpkg/info/apturl-common*

```

```

$ sudo dpkg --remove --force-remove-reinstreq apturl-common

dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: warning: files list file for package `libfaad2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libprotoc5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86vm1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiw30' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-khmeros-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xml-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireless-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-django-tagging' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkate1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libndesk-dbus-glib1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86misc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apturl-common' missing, assuming package has no files currently installed.
(Reading database ... 275353 files and directories currently installed.)
Removing apturl-common ...


```

```
$ sudo apt-get install apturl-common
```

---

