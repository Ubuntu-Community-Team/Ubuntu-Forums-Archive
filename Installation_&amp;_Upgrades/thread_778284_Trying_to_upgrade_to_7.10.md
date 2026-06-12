---
title: "Trying to upgrade to 7.10"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Spoken on 2008-05-01
ok, so i had some BIG issues upgrading to 8.04 and had to restore my computer to 7.04.
im trying to upgrade back up to 7.10 through update manager but when the upgrade process starts, i get this error message

```

Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)

```

it says i should check my network connection, but how could i be posting this if i didnt have one?

============================================================================
UPDATED INFORMATION BELOW
===========================================================================
ok so i used terminal to open update manager

i used 

```

sudo update-manager -c -d

```

it opened update manager, and i selected the 7.10 upgrade.  and it still stopped and gave me the error above.  but here is the output i got in terminal.

```

warning: could not initiate dbus
extracting '/tmp/tmpZUqUJs/gutsy.tar.gz'
authenticate '/tmp/tmpZUqUJs/gutsy.tar.gz' against '/tmp/tmpZUqUJs/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


```

---

