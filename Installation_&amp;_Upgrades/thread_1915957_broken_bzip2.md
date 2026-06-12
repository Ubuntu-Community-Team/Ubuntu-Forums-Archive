---
title: "broken bzip2"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by ketiv78 on 2012-01-27
sth is wrong with my Natty- I cannot install any packages, for example:
```
sudo apt-get install fail2ban
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  bzip2
Suggested packages:
  bzip2-doc python-gamin
The following NEW packages will be installed:
  fail2ban
The following packages will be upgraded:
  bzip2
1 upgraded, 1 newly installed, 0 to remove and 50 not upgraded.
20 not fully installed or removed.
Need to get 96.7 kB/133 kB of archives.
After this operation, 840 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://pl.archive.ubuntu.com/ubuntu/ natty/universe fail2ban all 0.8.4-3 [96.7 kB]
Fetched 96.7 kB in 0s (136 kB/s)
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `bzip2': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
```
I've tried cleaning options:
sudo apt-get clean
sudo dpkg --configure -a
..and also change bzip2 in status file (like described [http://ubuntuforums.org/archive/index.php/t-1232143.html](http://ubuntuforums.org/archive/index.php/t-1232143.html)) but no luck :(
What else can I do?

---

### Post by raja.genupula on 2012-01-27
I think you have some broken packages.
please do
```
sudo apt-get install -f
```
Let us know what you got .
All the best. :)

---

### Post by ketiv78 on 2012-01-27
```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  bzip2
Suggested packages:
  bzip2-doc
The following packages will be upgraded:
  bzip2
1 upgraded, 0 newly installed, 0 to remove and 50 not upgraded.
20 not fully installed or removed.
Need to get 0 B/35.9 kB of archives.
After this operation, 164 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `bzip2': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
```
:(

---

### Post by ketiv78 on 2012-01-27
I think I've found a cause- it's corrupted bzip2.list file, but I cannot delete it. I know that I should do repair filesystem by fsck, but it's remote machine and I can't umount / partition.
Is there a way to delete that file without fsck?

```
#ls-l
[...]
-rw-r--r-- 1 root root    2192 Jun 17  2011 byobu.templates
-????????? ? ?    ?          ?            ? bzip2.list
-rw-r--r-- 1 root root     705 Jan 27 11:15 bzip2.list-new
-rw-r--r-- 1 root root    1086 Feb 20  2011 bzip2.md5sums
-rwxr-xr-x 1 root root     203 Feb 20  2011 bzip2.postinst
-rwxr-xr-x 1 root root     543 Feb 20  2011 bzip2.preinst
-rwxr-xr-x 1 root root     141 Feb 20  2011 bzip2.prerm

# rm bzip2.list
rm: cannot remove `bzip2.list': Input/output error
```

---

### Post by ketiv78 on 2012-01-27
solved: 
1. I renamed /var/dpkg/info directory into /var/dpkg/info_trash,
2. I made a new dir /var/dpkg/info and I copied all files from /var/dpkg/info_trash exept corrupted bzip2.list
3. sudo apt-get install -f and voila! \\:D/

---

### Post by raja.genupula on 2012-01-28
Thats really a Good news man , please mark the thread as solved from thread tools.

---

