---
title: "Apt-get over SSH"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by gineraso on 2007-04-12
My server is locked down to only SSH access,and the only port listening is the SSH port.  Is it possible to use apt-get to download updates and other applications in this situation?

Thank you. 

Gineraso

---

### Post by solar george on 2007-04-12
Just SSH in and try (can't see why you shouldn't be able to)

---

### Post by Snowin on 2007-04-12
> **gineraso said:**
> My server is locked down to only SSH access,and the only port listening is the SSH port.  Is it possible to use apt-get to download updates and other applications in this situation?

Thank you. 

Gineraso

That very much depends on how outbound connections are configured on your server.  Generally speaking "sudo apt-get update" followed by "sudo apt-get dist-upgrade" should be fine, unless the server is blocking outbound connections.

It is possible to lock a server down so that it can't make outbound connections.  Any apt-get update which fails shouldn't do any harm to your system though, so give it a whirl and see what happens.

---

### Post by gineraso on 2007-04-12
I get these errors:

user@host:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Snowin on 2007-04-12
> **gineraso said:**
> I get these errors:

user@host:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

The chances are then that outbound connections are limited. Do you administer this machine yourself or does someone else do that for you?

---

### Post by gineraso on 2007-04-12
I'm the administrator.  I was told by the networking team that only ssh was allowed in.

---

### Post by gineraso on 2007-04-13
Just spoke to the networking folks and yes, all outbound traffic is blocked.  Is there a way I can download the updates to a flash device then install them?

---

