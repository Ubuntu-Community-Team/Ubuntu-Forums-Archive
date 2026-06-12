---
title: "checkbox package broken, leaving system in broken state"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kahrn on 2009-03-13
On attempt to upgrade my system to alpha 6 I am greeted with a bunch of errors relating to computer-janitor, hwtest, python-fst, checkbox, and checkbox-gtk. 

It appears that the checkbox package is broken. Removing all the offending packages will halt the errors. 

Attempting to install checkbox again to resolve all the other packages will result in errors. 

```
Need to get 0B/74.6kB of archives.
After this operation, 1249kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 182558 files and directories currently installed.)
Unpacking checkbox (from .../archives/checkbox_0.5_all.deb) ...
dpkg: serious warning: files list file for package `checkbox' missing, assuming package has no files currently installed.
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2151, in <module>
    main()
  File "/usr/bin/pycentral", line 2145, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1493, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 855, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing /var/cache/apt/archives/checkbox_0.5_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/checkbox_0.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

apt-get -f install does not work, and i have cleaned my cache. Is this just a case of a broken package? Is anyone else having this problem?

---

### Post by lamborghiniwang on 2009-03-13
> **kahrn said:**
> On attempt to upgrade my system to alpha 6 I am greeted with a bunch of errors relating to computer-janitor, hwtest, python-fst, checkbox, and checkbox-gtk. 

It appears that the checkbox package is broken. Removing all the offending packages will halt the errors. 

Attempting to install checkbox again to resolve all the other packages will result in errors. 

```
Need to get 0B/74.6kB of archives.
After this operation, 1249kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 182558 files and directories currently installed.)
Unpacking checkbox (from .../archives/checkbox_0.5_all.deb) ...
dpkg: serious warning: files list file for package `checkbox' missing, assuming package has no files currently installed.
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2151, in <module>
    main()
  File "/usr/bin/pycentral", line 2145, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1493, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 855, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing /var/cache/apt/archives/checkbox_0.5_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/checkbox_0.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

apt-get -f install does not work, and i have cleaned my cache. Is this just a case of a broken package? Is anyone else having this problem?

I am sadly reporting that I'm having the same issue. It seems to be related to this bug report:
[https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/320991](https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/320991)

---

### Post by rajeev1204 on 2009-03-13
Just open synaptic and fix broken packages.

then reload using main server repo. or sudo apt-get update

---

