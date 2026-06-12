---
title: "Deskbar-applet update fails"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by Valshar on 2008-09-28
Well, I've done some searches and couldn't really find an answer that solved the problem, so I've decided to post it. I'm not sure if this is the right section for this, but here goes:

When I update, the deskbar-applet fails to upgrade. On the terminal I get this:

```
andre@andre:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  deskbar-applet
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/330kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 117445 files and directories currently installed.)
Preparing to replace deskbar-applet 2.22.2.1-0ubuntu1 (using .../deskbar-applet_2.22.3.1-0ubuntu1_i386.deb) ...
/usr/share/gconf/schemas/deskbar-applet.schemas:1: parser error : Start tag expected, '<' not found
clear    Mod1
^
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1891, in <module>
    main()
  File "/usr/bin/pycentral", line 1885, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1333, in run
    old_pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 303, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 332, in read_pyfiles
    self.pkgconfig.readfp(file(config_file))
  File "/usr/lib/python2.5/ConfigParser.py", line 286, in readfp
    self._read(fp, filename)
  File "/usr/lib/python2.5/ConfigParser.py", line 462, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /usr/share/pyshared-data/deskbar-applet, line: 1
'keycode   9 = 0 section notsign\n'
dpkg: error processing /var/cache/apt/archives/deskbar-applet_2.22.3.1-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1891, in <module>
    main()
  File "/usr/bin/pycentral", line 1885, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1242, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 303, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 332, in read_pyfiles
    self.pkgconfig.readfp(file(config_file))
  File "/usr/lib/python2.5/ConfigParser.py", line 286, in readfp
    self._read(fp, filename)
  File "/usr/lib/python2.5/ConfigParser.py", line 462, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /usr/share/pyshared-data/deskbar-applet, line: 1
'keycode   9 = 0 section notsign\n'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/deskbar-applet_2.22.3.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyone know how to solve this? I'd be grateful!

---

### Post by Valshar on 2008-10-01
Anyone...?

---

### Post by Valshar on 2008-10-04
One last try... really wanted to fix this :/

---

### Post by Valshar on 2008-10-12
I have yet to solve this.

---

