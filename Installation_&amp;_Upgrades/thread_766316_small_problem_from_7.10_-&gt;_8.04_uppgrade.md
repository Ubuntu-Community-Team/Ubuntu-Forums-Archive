---
title: "small problem from 7.10 -&gt; 8.04 uppgrade"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by tinker-t on 2008-04-25
Hi folks,

I've just completed an upgrade to Hardy, and all is working well apart from one small thing - gedit wont get upgraded.

If I try and install gedit from the command line, this is what I get:

```
ian@ian:~$ sudo apt-get install gedit
[sudo] password for ian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gedit
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/736kB of archives.
After this operation, 69.6kB disk space will be freed.
(Reading database ... 147919 files and directories currently installed.)
Preparing to replace gedit 2.20.3-0ubuntu1 (using .../gedit_2.22.1-0ubuntu1_i386.deb) ...
Unpacking replacement gedit ...
dpkg: error processing /var/cache/apt/archives/gedit_2.22.1-0ubuntu1_i386.deb (--unpack):
 unable to make backup link of `./usr/bin/gedit' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gedit_2.22.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@ian:~$
```


So the problem seems to lie in the fact that dpkg is having trouble removing the old version of gedit before installing the new version.

If I even just try to remove /usr/bin/gedit as root, that *still* fails!:

```
ian@ian:~$ sudo rm -f /usr/bin/gedit 
rm: cannot remove `/usr/bin/gedit': Operation not permitted
ian@ian:~$
```

I have tried deleting (and restoring!) other files in /usr/bin, which does work OK - the problem does seem confined to this one file.

Here's some stuff that might help:


```
ian@ian:~$ ls -l /usr/bin/gedit 
-rwxr-xr-x 1 root root 636992 2007-10-22 16:54 /usr/bin/gedit


ian@ian:~$ ls -l /usr/ | grep bin
drwxr-xr-x   2 root root 69632 2008-04-25 09:43 bin
```

I've searched these boards / google and can't seem to find anything relevant - any help / suggestions / pointers to threads I've missed would be appreciated!

---

### Post by prshah on 2008-04-25
> **tinker-t said:**
> 
If I try and install gedit from the command line, this is what I get:

If I even just try to remove /usr/bin/gedit as root, that *still* fails!:
```
ian@ian:~$ ls -l /usr/bin/gedit 
-rwxr-xr-x 1 root root 636992 2007-10-22 16:54 /usr/bin/gedit
ian@ian:~$ ls -l /usr/ | grep bin
drwxr-xr-x   2 root root 69632 2008-04-25 09:43 bin
```


Everything looks OK, my gedit is also the same size; maybe a recovery mode delete is called for ?

If that fails, a simple fsck (filesystem check)?

---

