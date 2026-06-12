---
title: "Can't get updates on a new server install"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by wxman on 2007-10-23
Has anyone had this problem? 
Installing 6.06 server, going along fine till I do the apt-get update. All I keep getting is:

```

Err http://us.archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://security.ubuntu.com dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

I've tried it several times with the same results. I did a ping of a known IP address on the Internet just to be sure I was connected, and it came back ok.

---

### Post by wxman on 2007-10-23
Never mind, I fixed it myself. I forgot to edit the /etc/resolv.conf file to show my ISP DNS IP addresses.

---

