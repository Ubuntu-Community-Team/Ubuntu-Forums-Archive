---
title: "OSDisc installrepo problems"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by rupertwbrown on 2013-12-28
Hello - I've got a terrible internet connection at home so bought the OSDisc 16 DVD repository for Ubuntu 13.10.  I'm following their instructions in the ReadMe file on the first disc - but just cannot get a program called installrepo to run.  Please see below - "no such file or directory".  What am I missing here?

rupert/$ ls -la tmp
total 64
drwxrwxrwt  8 root   root    4096 Dec 28 19:49 .
drwxr-xr-x 23 root   root    4096 Dec 27 14:58 ..
drwxrwxrwt  2 root   root    4096 Dec 28 18:25 .ICE-unix
-rwxr-xr-x  1 rupert rupert 25620 Dec 28 19:20 installrepo
drwx------  2 root   root    4096 Dec 28 18:24 pulse-PKdhtXMmr18n
drwx------  2 rupert rupert  4096 Dec 28 18:25 ssh-45cNhiEkk19T
drwx------  2 rupert rupert  4096 Dec 28 19:45 tmp5jrzgb
drwx------  2 root   root    4096 Dec 28 18:40 tmpaftmur
-rw-------  1 rupert rupert     0 Dec 28 18:26 tmpzWxwuk
-rw-rw-r--  1 rupert rupert     0 Dec 28 18:25 unity_support_test.0
-r--r--r--  1 root   root      11 Dec 28 18:24 .X0-lock
drwxrwxrwt  2 root   root    4096 Dec 28 18:24 .X11-unix
rupert$ sudo /tmp/installrepo -d /media/rupert/CDROM
[sudo] password for rupert: 
sudo: unable to execute /tmp/installrepo: No such file or directory

Thanks in advance.

---

### Post by varunendra on 2014-01-01
Welcome to the forums Rupert !

Sounds like a set of normal repository archive disks to me which can be manually added as a repository if not automatically detected as such when inserted. Could you post the contents of the "installrepo" script to let us see what it is supposed to do?

---

