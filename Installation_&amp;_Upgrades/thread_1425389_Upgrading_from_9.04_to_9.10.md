---
title: "Upgrading from 9.04 to 9.10"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by kelmos on 2010-03-09
Hi Guys,

I've done some searches and did find similar threads, but none with the issue that I have. I'm trying to do the upgrade but get the following error:

> 
root@server:~# do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool
Done Upgrade tool signature
Done downloading            
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 1
Debug information: 


gpg: Signature made Mon 02 Nov 2009 12:27:02 SAST using DSA key ID 437D05B5
gpg: /tmp/tmpQo7LG3/trustdb.gpg: trustdb created
gpg: BAD signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server. 
root@server:~#


Some assistance will be appreciated.

Thanks!

---

### Post by s.fox on 2010-03-09
Hello and welcome to the forum :D

[This]("http://ubuntuforums.org/showpost.php?p=8082071&postcount=2") post describes a solution for the same problem you are experiencing.  The problem was resolved by changing the mirror.

Does this work for you also?  :)

-Silver Fox

---

### Post by kelmos on 2010-03-09
Hi Silver_fox,

Thanks for the welcome. 

I've tried different mirrors as well and get the exact same error. I have however played around with the 'apt-keys' command and noticed that it is trying the same key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" even though I remove this key from the list. 

Any ideas on this?

---

