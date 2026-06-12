---
title: "Can't download SAMBA Security Fix"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by saransk on 2007-11-16
Tried to download the three SAMBA security updates and got these messages:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden

Going to the files directly gives a "Forbidden" message when I try to download

Is there a problem with the security fix?

:confused:

---

### Post by taurus on 2007-11-16
[http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)
[http://ubuntuforums.org/showthread.php?t=463944](http://ubuntuforums.org/showthread.php?t=463944)

---

### Post by PLiNkO on 2007-11-16
Same Here

---

### Post by qpieus on 2007-11-16
there's another post around that says the security fix had a bug in it that needs fixing, so it got yanked from the repo servers, that's why you're getting the 403 error. It'll be fixed and put back on the servers soon I'm sure.

---

