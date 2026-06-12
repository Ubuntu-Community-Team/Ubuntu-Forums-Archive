---
title: "how to solve apt-get update error"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by mady03sam on 2010-01-27
[SIZE=3]:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
  Could not connect to 202.62.73.208:4443 (202.62.73.208 . - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)
Reading package lists... Done                   
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 202.62.73.208:4443 (202.62.73.208. - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

...................... and im not using 202.62.73.208 ip so help me out from this
[/SIZE]

---

### Post by lidex on 2010-01-27
If it worked before, it'll work again. Just give it time. These things usually resolve themselves. If impatient, however, try selecting a different server in software sources.

BTW, do you still have Dapper installed? If not you should remove those entries.

---

### Post by mady03sam on 2010-01-28
if im changing http to ftp in /etc/apt/source.list then its getting worked where as gettin connect to another new server the same error im getting tell me how to resolve dis kind of issues..................n moreover im not using 202.62.73.208 it is ma old configuration n i also changed ma network/interfaces with the new ip.......... n thanks fr sending reply.

---

### Post by lidex on 2010-01-28
All my sources are http and they work fine. Are you behind a proxy server?

---

### Post by mady03sam on 2010-02-02
> **lidex said:**
> All my sources are http and they work fine. Are you behind a proxy server?
nop i dont have any proxy still im getting this kindoff errors.................yesterday i checked once again n its showing me same issue again but when i change http to ftp its working fine i dont know why this hell is happening with ma PC, chnaging to another server is also giving same issue it can be rectified only by changing url http to ftp........so anybody give me permanent solution

---

### Post by lidex on 2010-02-03
Same situation solved here:
[http://ubuntuforums.org/showthread.php?t=1388174]("http://ubuntuforums.org/showthread.php?t=1388174")

---

