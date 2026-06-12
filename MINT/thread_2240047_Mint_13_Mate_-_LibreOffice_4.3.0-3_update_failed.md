---
title: "Mint 13 Mate - LibreOffice 4.3.0-3 update failed"
date: 2014-08-17
forum: MINT
---

### Post by danielr2 on 2014-08-17
I installed the latest LibreOffice updates last night through Update Manager but the the update failed with broken dependencies. 

When trying to update libreoffice-core, Update Manager returns the following error: 
```
E: /var/cache/apt/archives/libreoffice-base_1%3a4.3.0-3ubuntu1~precise1_i386.deb: trying to overwrite '/usr/lib/libreoffice/share/basic/script.xlc', which is also in package libreoffice-common 1:4.3.0-3ubuntu1~precise1
```

Here is the detailed output from Update Manager
```

Selecting previously unselected package libreoffice-base.
(Reading database ... 250139 files and directories currently installed.)
Preparing to replace libreoffice-base 1:4.3.0-0ubuntu1~precise1 (using .../libreoffice-base_1%3a4.3.0-3ubuntu1~precise1_i386.deb) ...
Unpacking replacement libreoffice-base ...
dpkg: error processing /var/cache/apt/archives/libreoffice-base_1%3a4.3.0-3ubuntu1~precise1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libreoffice/share/basic/script.xlc', which is also in package libreoffice-common 1:4.3.0-3ubuntu1~precise1
No apport report written because MaxReports is reached already
                                                              dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error: --compare-versions takes three arguments: <version> <relation> <version>

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-base_1%3a4.3.0-3ubuntu1~precise1_i386.deb
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

After some Internet research, purging and reinstalling of LibreOffice seemed to be the solution. So I tried ```
sudo apt-get purge libreoffice*
``` followed by ```
sudo apt-get -f install
``` then again ```
sudo apt-get purge libreoffice*
``` and finally ```
sudo apt-get install libreoffice
``` 
Below is the output of the 4 commands (I have omitted the long listings of LO components): 

```

~ $ sudo apt-get purge libreoffice*
[...]
  libreoffice-writer* python-uno* unoconv*
0 upgraded, 0 newly installed, 27 to remove and 30 not upgraded.
1 not fully installed or removed.
After this operation, 340 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 250137 files and directories currently installed.)
Removing libreoffice-base ...
No diversion 'diversion of /usr/lib/libreoffice/share/basic/dialog.xlc to /usr/lib/libreoffice/share/basic/dialog.xlc.noaccess by libreoffice-base', none removed.
No diversion 'diversion of /usr/lib/libreoffice/share/basic/script.xlc to /usr/lib/libreoffice/share/basic/script.xlc.noaccess by libreoffice-base', none removed.
/var/lib/dpkg/info/libreoffice-base.postrm: 31: /var/lib/dpkg/info/libreoffice-base.postrm: Syntax error: end of file unexpected (expecting "fi")
dpkg: error processing libreoffice-base (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libreoffice-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libreoffice-base
0 upgraded, 0 newly installed, 1 to remove and 30 not upgraded.
1 not fully installed or removed.
After this operation, 6,748 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 250137 files and directories currently installed.)
Removing libreoffice-base ...
No diversion 'diversion of /usr/lib/libreoffice/share/basic/dialog.xlc to /usr/lib/libreoffice/share/basic/dialog.xlc.noaccess by libreoffice-base', none removed.
No diversion 'diversion of /usr/lib/libreoffice/share/basic/script.xlc to /usr/lib/libreoffice/share/basic/script.xlc.noaccess by libreoffice-base', none removed.
/var/lib/dpkg/info/libreoffice-base.postrm: 31: /var/lib/dpkg/info/libreoffice-base.postrm: Syntax error: end of file unexpected (expecting "fi")
dpkg: error processing libreoffice-base (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libreoffice-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

~ $ sudo apt-get purge libreoffice*
[...]
  libreoffice-writer* python-uno* unoconv*
0 upgraded, 0 newly installed, 27 to remove and 30 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

```

```

~ $ sudo apt-get install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libreoffice-base libreoffice-report-builder-bin
Suggested packages:
  hyphen-hyphenation-patterns libreoffice-grammarcheck libreoffice-l10n-4.3
  myspell-dictionary mythes-thesaurus openclipart-libreoffice pstoedit
  libreoffice-officebean libreoffice-gcj libreoffice-report-builder
The following NEW packages will be installed:
  libreoffice libreoffice-report-builder-bin
The following packages will be upgraded:
  libreoffice-base
1 upgraded, 2 newly installed, 0 to remove and 30 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

```

Any idea how I can fix this update problem? The libreoffice-base update constantly fails and, according to Synaptic, the libreoffice-core also seems to have a problem with broken dependencies.

---

### Post by ajgreeny on 2014-08-17
This can be solved relatively easily, and is the result of a system file missing one line.

Edit that file as root and you will then be able to uninstall libreoffice-base and then reinstall it.

See 
[http://ubuntuforums.org/showthread.php?t=2239916&p=13100243#post13100243](http://ubuntuforums.org/showthread.php?t=2239916&p=13100243#post13100243)
[http://ubuntuforums.org/showthread.php?t=2239841](http://ubuntuforums.org/showthread.php?t=2239841)
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1354557](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1354557)
for the details.

---

### Post by danielr2 on 2014-08-17
Thank's a lot, that did the trick.

---

