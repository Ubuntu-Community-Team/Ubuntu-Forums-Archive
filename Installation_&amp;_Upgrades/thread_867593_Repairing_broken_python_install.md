---
title: "Repairing broken python install"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by g.caltech on 2008-07-23
Hello,
I am running 7.10. I installed python 2.5.2 over the 2.5.1 version that comes with Ubuntu. However, now various packages are not working with the new version, so I'd like to return to the version that comes with Ubuntu. I tried:
sudo aptitude -vv reinstall python2.5
which yields:
The following packages are unused and will be REMOVED:
  python-numarray python-wxgtk2.6
The following packages have been automatically kept back:
  libgnutls-dev libgnutlsxx13 libpcre3-dev libpcrecpp0 libpq-dev
  libwxbase2.8-0 libwxgtk2.8-0 libxfcegui4-4 linux-libc-dev
  linux-restricted-modules-common openssl-blacklist python-wxversion smbfs
  wireshark-common xserver-xorg-core xserver-xorg-dev
The following packages have been kept back:
  bind9-host dnsutils firefox libbind9-30 libdns32 libgnutls13 libisc32
  libisccc30 libisccfg30 liblwres30 libpcre3 libpq5 libruby1.8 libsmbclient
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic linux-ubuntu-modules-2.6.22-14-generic
  python-wxgtk2.8 rdiff-backup ruby1.8 samba samba-common smbclient tzdata
  wireshark
The following packages will be REINSTALLED:
  python2.5
The following partially installed packages will be configured:
  python-setuptools
0 packages upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 43 not upgraded.
Need to get 0B/2991kB of archives. After unpacking 18.5MB will be freed.
Do you want to continue? [Y/n/?]
Writing extended state information... Done
(Reading database ... 143734 files and directories currently installed.)
Removing python-numarray ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 953, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-numarray (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 875, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing python-wxgtk2.6 ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 953, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-wxgtk2.6 (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 python-numarray
 python-wxgtk2.6
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done


It seems that uninstalling these unneeded packages requires the wrong version of python, and is thus failing.

Please let me know how I can get back to python 2.5.1

Thank you,
G

---

### Post by yanom on 2009-03-18
typically you don't have to install python 2.x.z over python 2.x.y . The package maintainers usually add really important updates.

---

