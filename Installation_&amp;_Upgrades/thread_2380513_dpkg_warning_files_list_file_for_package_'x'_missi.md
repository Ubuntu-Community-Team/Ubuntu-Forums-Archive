---
title: "dpkg warning: files list file for package 'x' missing"
date: 2017-12-18
forum: Installation &amp; Upgrades
---

### Post by tho4 on 2017-12-18
I get the following error message when trying to download a package:
[HTML]dpkg: warning: files list file for package 'python-gtk2' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'curl' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/HTML]

It seems to be an error during an installation. I tried the following without success:
sudo apt-get -f install -> no change observed
dpkg --configure -a -> no change observed
sudo apt upgrade -> I get the same error message. 
I tried to remove the python-gtk2 package as follows:
[HTML]sudo dpkg --remove --force-remove-reinstreq python-gtk2
dpkg: dependency problems prevent removal of python-gtk2:
 dropbox depends on python-gtk2 (>= 2.12).
 python-glade2 depends on python-gtk2 (= 2.24.0-4ubuntu1).

dpkg: error processing package python-gtk2 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 python-gtk2
[/HTML]

Any suggestions welcome

---

### Post by deadflowr on 2017-12-18
Try going in the opposite direction
```
sudo apt-get update
sudo apt-get install --reinstall python-gtk2
```

---

### Post by tho4 on 2017-12-18
I get the same error message as above when I try to reinstall python-gtk2. Any over suggestions?

---

### Post by deadflowr on 2017-12-19
Is the error still showing something about curl?
That might be where the problem lies:
look over this
[https://askubuntu.com/questions/909719/dpkg-unrecoverable-fatal-error-aborting-files-list-file-for-package-linux-ge]("https://askubuntu.com/questions/909719/dpkg-unrecoverable-fatal-error-aborting-files-list-file-for-package-linux-ge")
in you case the files would relate to curl,
like /var/lib/dpkg/info/curl.list

see if that helps clear it up.

Note you might try moving the file(s) first rather than outright deleting, just to be safe.

---

### Post by tho4 on 2017-12-20
Thanks for the advice, I moved the files from /var/lib/dpkg/info/ but then the error message appeared with another package (bluez), I moved it from the folder and the error message appeared with another package... So I'm still stuck.

---

