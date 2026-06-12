---
title: "error when trying to install ANYTHING"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by asus on 2006-11-05
i get this at the bottom of any instalation. .and the install seams to fail... i think its when i tried to upgrade to GAIM 2.0 .. i screwed something up. .here is what i get


```
Setting up gaim (1.5.0+1.5.1cvs20051015-1ubuntu10) ...
rmdir: /usr/share/doc/gaim: Directory not empty
dpkg: error processing gaim (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gaim
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gaim (1.5.0+1.5.1cvs20051015-1ubuntu10) ...
rmdir: /usr/share/doc/gaim: Directory not empty
dpkg: error processing gaim (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gaim
Previous command did not complete successfully. Exiting.

```

---

### Post by MWAAAHAAA on 2006-11-05
> rmdir: /usr/share/doc/gaim: Directory not empty

Try deleting the contents of the directory manually.

Question: how did you install GAIM 2.0?

---

### Post by asus on 2006-11-05
good call.. that worked :-) .. idk . .i tried compiling the source but it did not work.. i told me it could not make an exicutibal using gcc or something ??

---

### Post by asus on 2006-11-05
now i have another problem. .i maneged to get gaim 2.0 install using this tutorial

[http://www.supriyadisw.net/2006/10/gaim-20-beta-on-ubuntu-dapper](http://www.supriyadisw.net/2006/10/gaim-20-beta-on-ubuntu-dapper)


now i am getting this error

```
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gaim: Depends: gaim-data (= 2:2.0.0beta3.1-0ubuntu1) but 1:1.5.0+1.5.1cvs20051015-1ubuntu10 is installed
E: Unmet dependencies. Try using -f.

```

u do sudo apt-get install  -f

and i get
```
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gaim-data
The following packages will be upgraded:
  gaim-data
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
Need to get 0B/4273kB of archives.
After unpacking 1725kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 80848 files and directories currently installed.)
Preparing to replace gaim-data 1:1.5.0+1.5.1cvs20051015-1ubuntu10 (using .../gaim-data_2%3a2.0.0beta3.1-0ubuntu1_all.deb) ...
Unpacking replacement gaim-data ...
dpkg: error processing /var/cache/apt/archives/gaim-data_2%3a2.0.0beta3.1-0ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/aclocal/gaim.m4', which is also in package gaim-devel
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gaim-data_2%3a2.0.0beta3.1-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


apparently i can't install or upgrade anything until i fix this?

---

### Post by MWAAAHAAA on 2006-11-05
You could try 'apt-get remove gaim-devel'.

On a side note, in my experience 'unofficial' packages are usually much more trouble than they're worth. It is usually better to compile from source and install to /usr/local than to mess up your dependencies using some unsupported package.
You said you had a problem with gcc not being able to create executables. Search this forum for a solution as it is quite common and try compiling from source again.

---

