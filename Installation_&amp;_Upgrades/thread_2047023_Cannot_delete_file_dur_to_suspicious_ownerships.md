---
title: "Cannot delete file dur to suspicious ownerships"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by CDrewing on 2012-08-24
Hi,

after fsck I got the problem that I cannot delete the file /usr/bin/boincmgr due to suspicious ownerships. See yourself:

```
cdrewing@cdrewing-desktop:/usr/bin$ ls -l boinc*
-rwxr-xr-x 1 root root 841992 Jul 18 19:24 boinc
-rwxr-xr-x 1 root root 227368 Jul 18 19:24 boinccmd
-rwxr-xr-x 1 root  256   4096 Mai 20  1986 boincmgr

```

No need to mention that there is no group 256.

When I try to delete/change the file I receive:

```
cdrewing@cdrewing-desktop:/usr/bin$ sudo rm -f /usr/bin/boincmgr
[sudo] password for cdrewing: 
rm: Entfernen von »/usr/bin/boincmgr“ nicht möglich: Die Operation ist nicht erlaubt

```

Note: Translated this means "rm: removal of '/usr/bin/boincmgr' not possible: The operation is not permitted"

I even tried to remove the file using a LiveCD where I am receiving the same error. Even chown to root:root is not working.

Does anyone have an idea how to delete this file (as I want to make needed updates on boincmgr) without wiping my whole drive (and installing the system completely from scratch as well)?

Thank you for your help.

Rgds
Christian

---

### Post by SlugSlug on 2012-08-24
try 

```
sudo -i
```

```
rm /path/file
```

---

### Post by DieEier on 2012-10-05
Maybe try 
lsattr test   /usr/bin/boincmgr
If you see something like this it means that the imutable flag is set on this file ( indicated by the i ). This is like being made read only.
----i--------e-  /usr/bin/boincmgr

To remove the immutable flag do 
sudo chattr -i  /usr/bin/boincmgr

If you are unsure about what the file does then it may be a good idea to go 
mv  /usr/bin/boincmgr  /usr/bin/boincmgr.back 
this will rename the file so that you can put it back in play if something breaks. May be safer than just removing.
Hope this helps

---

