---
title: "[SOLVED] How do I fix broken package python-uno?"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by otakuj462 on 2007-07-13
Hi, I'm running Kubuntu Edgy and I just ran apt-get update. One of the packages set to install was the new openoffice. Unfortunately, upgrade failed (I'm not sure why), and since then, I have been unable to get apt to work due to broken package python-uno.
I have tried the following:
```
jacob@jacob-laptop:/usr/local/bin$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-virtkey python-gconf
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-uno
The following packages will be upgraded:
  python-uno
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0B/220kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 209751 files and directories currently installed.)
Preparing to replace python-uno 2.0.4-0ubuntu5 (using .../python-uno_2.0.4-0ubuntu6_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in <module>
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in <module>
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: error processing /var/cache/apt/archives/python-uno_2.0.4-0ubuntu6_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-uno_2.0.4-0ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
```
jacob@jacob-laptop:/usr/local/bin$ sudo dpkg -r python-uno
(Reading database ... 209748 files and directories currently installed.)
Removing python-uno ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in <module>
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: error processing python-uno (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 python-uno

```
I also ran dpkg-reconfigure -a, which failed while trying to reconfigure pureftpd.

It seems like I cannot use apt-get until this broken package is fixed or removed. But I don't know any other way to fix the package other than using apt-get. So I feel like I'm stuck, and I may need to use a more low-level configuration tool... but what is more low-level than dpkg?

If anyone has any advice, I would greatly greatly appreciate it if you would let me know.
Thanks.

Jake

---

### Post by otakuj462 on 2007-07-13
Managed to fix the problem by manually upgrading to Feisty Fawn. Went into /etc/apt/sources.list and changed all of the references from "edgy" to "feisty". Ran apt-get update, apt-get install -f, then apt-get dist-upgrade. Now apt seems to work again. Also, Ubuntu Feisty is amazing!

---

