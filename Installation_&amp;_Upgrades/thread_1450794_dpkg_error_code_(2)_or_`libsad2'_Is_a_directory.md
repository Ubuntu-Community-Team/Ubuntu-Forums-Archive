---
title: "dpkg error code (2) or `libsad2': Is a directory"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by irmiev on 2010-04-09
Hi all

When I try to install something using apt-get or from package using dpkg I always receive 
the same error...

For instance:

```
sudo apt-get install jedit
```and when the OS reach the point for unpacking and installing the package the output is:

```
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `libsad2': Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```I will appreciate your help...

---

### Post by lalejand on 2011-07-10
I have the same problem ! Did you solve it ? how ?

---

### Post by lalejand on 2011-07-10
Just solved it.

I created the file /var/lib/dpkg/info/xdg-utils.list and pasted what I found there : [http://ns2.canonical.com/fr/natty/all/xdg-utils/filelist](http://ns2.canonical.com/fr/natty/all/xdg-utils/filelist)

Looks like the file had been transformed into a folder with a .db inside !?

---

