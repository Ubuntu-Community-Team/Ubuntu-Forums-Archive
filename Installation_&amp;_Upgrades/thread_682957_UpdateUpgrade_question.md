---
title: "Update/Upgrade question"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by behrk2 on 2008-01-30
Hey guys,

I am running a web server on Ubuntu Server 7.10.

I have to make an upgrade to mod_ssl.

I cannot seem to do so, however. Here are two of my attempts:

```

behrk2@rlms:~$ sudo apt-get install apache2 libapache-mod-ssl                   
Reading package lists... Done
Building dependency tree
Reading state information... Done
apache2 is already the newest version.
Package libapache-mod-ssl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache-mod-ssl has no installation candidate
behrk2@rlms:~$

```

```

behrk2@rlms:~$ sudo apt-get install libapache-mod-ssl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libapache-mod-ssl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache-mod-ssl has no installation candidate
behrk2@rlms:~$

```

For some reason, I can't find anything about this issue on the internet. And I have been unable to find any other way to update my mod_ssl (from 2.2.4 to 2.8.22).

Any ideas? Thanks!

---

### Post by taurus on 2008-01-30
Maybe you didn't have all the repos available in /etc/apt/sources.list.

Edit /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with deb & deb-src.  Save it with <Ctrl>o and exit with <Ctrl>x.

Then, update the repos with

```
sudo apt-get update
```
Now, see if you can install anything at all.

---

### Post by behrk2 on 2008-01-30
Thanks taurus,

I tried that out, and still the same result! Ahh.

---

