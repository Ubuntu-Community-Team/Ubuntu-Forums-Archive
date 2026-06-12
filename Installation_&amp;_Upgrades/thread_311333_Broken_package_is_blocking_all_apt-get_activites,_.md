---
title: "Broken package is blocking all apt-get activites, can't install any other software"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by calvmari on 2006-12-02
Hey all!

I'm really in a bind, any help would be appreciated. So I have a package that's marked for removal, but something's wrong, some files are missing. So as a result, every time I try to use apt-get to install a program or uninstall a program, it tries to finish this package removal first then quits.

The package in question is mfc8500lpr-1.1.2-1.i386.deb (it's a driver for a brother printer I no longer needed)

I didn't delete anything myself, I didn't touch any of the installation, everything was done by apt-get or the package manager GUI. Does anyone know how I can force this package out or skip its removal to use apt-get to install my other software? Thank you!

By the way, here's the console when I try to remove it.

```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree... Done
The following packages were automatically installed and are no longer required:
  mfc8500lpr
The following packages will be REMOVED:
  mfc8500lpr
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 114777 files and directories currently installed.)
Removing mfc8500lpr ...
/var/lib/dpkg/info/mfc8500lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc8500lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8500lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
calvmari@Micho:~$ 

```

   -calvmari

---

### Post by calvmari on 2006-12-03
Ha, solved my own problem. Posted my solution to someone else who had the same problem: [http://www.ubuntuforums.org/showpost.php?p=1838138&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1838138&postcount=3)

---

