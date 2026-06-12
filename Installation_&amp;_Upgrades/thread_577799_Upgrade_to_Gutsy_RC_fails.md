---
title: "Upgrade to Gutsy RC fails"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by flarkit on 2007-10-16
Hi

I've attempted 5x to do "update-manager -d" and each fails on the authentication. I've tried doing this whilst logged in as myself, then as 'root'. Each time I've also run 'gpg' first. Can anyone suggest why this happpens, please?

It gets to the "Downloading the upgrade tool" window, then fails and the following output:

>  sudo update-manager -c -d
warning: could not initiate dbus
extracting '/tmp/tmpzqaugo/gutsy.tar.gz'
authenticate '/tmp/tmpzqaugo/gutsy.tar.gz' against '/tmp/tmpzqaugo/gutsy.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 65536
Debug information: 

gpg: WARNING: unsafe permissions on homedir `/tmp/tmpzqaugo'

gpg: Signature made Fri 05 Oct 2007 22:32:21 SAST using DSA key ID 437D05B5
gpg: /tmp/tmpzqaugo/trustdb.gpg: trustdb created
gpg: BAD signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

---

### Post by por100pre1 on 2007-10-17
Try this:

```
gpg --keyserver subkeys.pgp.net --recv-keys 437D05B5
```

```
gpg --export --armor 437D05B5 | sudo apt-key add -
```

Hope it helps. Sorry for the delay.

---

### Post by flarkit on 2007-10-18
Thanks for the reply.

After I switched my PC on last night, I ran "update-manager -d" again and it simply started the upgrade once I clicked on the "Upgrade" button. I suppose there was something wrong with our local repo's before this.

I stopped after I saw it needed a 745Mb download though. That'll have to wait till next week...
:)

---

