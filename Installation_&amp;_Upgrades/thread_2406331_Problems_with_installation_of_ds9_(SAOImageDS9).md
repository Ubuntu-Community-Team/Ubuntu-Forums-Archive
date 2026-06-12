---
title: "Problems with installation of ds9 (SAOImageDS9)"
date: 2018-11-19
forum: Installation &amp; Upgrades
---

### Post by lucasfisico-a on 2018-11-19
Hi,
I'm new to this forum. My Ubuntu version's 14.04 trusty (x86-64).
I recently installed the IRAF program (which works with astronomical images) and need to set up a complementary program: the "ds9" (SAOImageDS9). When trying to run *ds9* for the first time, I get the following error:

> ds9: error while loading shared libraries: libssl.so.10

I've tried the following link tips but no success [https://istkb.adlinktech.com/article/error-libssl-10-missing-ubuntu-14/](https://istkb.adlinktech.com/article/error-libssl-10-missing-ubuntu-14/)

When I try to run the *ds9* program the following message appears:

> ds9: /lib/x86_64-linux-gnu/libcrypto.so.10: version `libcrypto.so.10' not found (required by ds9)
 ds9: /lib/x86_64-linux-gnu/libssl.so.10: version `libssl.so.10' not found (required by ds9)

During these attempts, errors appear in the package python-samba. When I install *libssl1.0.0* and *libssl-dev* packages, the following result appears:

> Reading package lists...Building dependency tree...
Reading state information...
libssl-dev is already the newest version.
libssl1.0.0 is already the newest version.
The following packages were automatically installed and are no longer required:
  apturl apturl-common attr libaio1 python-dnspython samba-dsdb-modules
  samba-vfs-modules tdb-tools
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-samba
The following packages will be upgraded:
  python-samba
1 upgraded, 0 newly installed, 0 to remove and 200 not upgraded.
38 not fully installed or removed.
Need to get 0 B/1395 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] (Reading database ... 609344 files and directories currently installed.)
Preparing to unpack .../python-samba_2%3a4.3.11+dfsg-0ubuntu0.14.04.17_amd64.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/python-samba_2%3a4.3.11+dfsg-0ubuntu0.14.04.17_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ModuleNotFoundError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-samba_2%3a4.3.11+dfsg-0ubuntu0.14.04.17_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 

I tried reinstalling *python-samba* but it gives the same error above. I suspect that conflicts are occurring with different versions of python that I have recently installed. The *software center* does not open too. And I can not change the repositories settings.
Can someone help me solve these problems, please?

---

### Post by olebole2 on 2018-11-20
I would recommend to upgrade to 18.04 LTS. There, you can install iraf and saods9 directly with apt.

---

