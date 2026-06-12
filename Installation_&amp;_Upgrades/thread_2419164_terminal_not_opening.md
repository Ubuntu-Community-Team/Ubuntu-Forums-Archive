---
title: "terminal not opening"
date: 2019-05-17
forum: Installation &amp; Upgrades
---

### Post by rcrahul60 on 2019-05-17
it has some problem with python as  i was trying to upgrade ubuntu so i changed some path 
now no commands are working from ALT+F2 also and terminal not opening i run this command from vscode terminal
```
tbosss@tbosss-550P5C-550P7C:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.18.0-17 linux-headers-4.18.0-17-generic linux-image-4.18.0-17-generic linux-modules-4.18.0-17-generic
  linux-modules-extra-4.18.0-17-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  python3-debconf
The following packages will be upgraded:
  python3-debconf
1 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
1 not fully installed or removed.
Need to get 0 B/4,060 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 250240 files and directories currently installed.)
Preparing to unpack .../python3-debconf_1.5.66ubuntu1_all.deb ...
/var/lib/dpkg/info/python3-debconf.prerm: 6: /var/lib/dpkg/info/python3-debconf.prerm: py3clean: not found
dpkg: warning: old python3-debconf package pre-removal script subprocess returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: py3clean: not found
dpkg: error processing archive /var/cache/apt/archives/python3-debconf_1.5.66ubuntu1_all.deb (--unpack):
 new python3-debconf package pre-removal script subprocess returned error exit status 127
/var/lib/dpkg/info/python3-debconf.postinst: 6: /var/lib/dpkg/info/python3-debconf.postinst: py3compile: not found
dpkg: error while cleaning up:
 installed python3-debconf package post-installation script subprocess returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/python3-debconf_1.5.66ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dino99 on 2019-05-17
Purge the python3 entries from :

> sudo gedit /var/lib/dpkg/status

you can find them via the Search feature; then logout/in and clean the system (clean/autoclean/autoremove/gtkorphan)  then update again

---

### Post by TheFu on 2019-05-17
You probably broke the PATH environment variable.  Create another account, see what the correct PATH should be, if you didn't make a backup of that data, file, information BEFORE hand.

You can always use the **/full/path/to/program** to run it. It becomes a hassle, but it works.
Rather than changing the PATH environment to deal with 1 program in a strange place, many people will
a) make a symbolic link for the program to their ~/bin/ directory or to /usr/local/bin/
b) make an alias that points to the full path to program

I use both. Just depends.

---

### Post by rcrahul60 on 2019-05-20
i tried creating another user account but terminal also not opening in that account

---

### Post by rcrahul60 on 2019-05-20
i also purge the entries

---

### Post by TheFu on 2019-05-20
> **rcrahul60 said:**
> i tried creating another user account but terminal also not opening in that account

I don't understand what you mean by either part of that statement. 
Please expand what this means.


> **rcrahul60 said:**
> 
    i also purge the entries 
What entries?  We can't accurately guess.

---

### Post by rcrahul60 on 2019-05-22
i just remove the 18.04 and reinstall the 19.04 but this version also have problem sometime it get stuck before login screen

---

