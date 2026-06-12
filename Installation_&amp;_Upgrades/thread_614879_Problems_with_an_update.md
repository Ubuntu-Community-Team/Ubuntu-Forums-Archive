---
title: "Problems with an update"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by rgeddes on 2007-11-16
I had a few updates pending from the update manager.  Some of them completed and some of them didn't.

The ones that did not complete generated this message:

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden



Do I need special permissions to access these packages?

---

### Post by ndereus on 2007-11-16
I can confirm this problem. It seems permissions on the download server do not permit read access on the file?

I can see the package I need - requesting the directory reveals a nice listing as usual.

[http://security.ubuntu.com/ubuntu/pool/main/s/samba/](http://security.ubuntu.com/ubuntu/pool/main/s/samba/)


However, trying to select package smbclient_3.0.26a-1ubuntu2.1_i386.deb returns a 403 "You don't have permission to access /ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb on this server."


Cheers,
  Nils

---

### Post by madsmeg on 2007-11-16
I too am having the same problem, must be a server down somewhere or something simple like that. I am sure this will be fixed soon.

---

### Post by madsmeg on 2007-11-16
[http://ubuntuforums.org/showpost.php?p=3783704&postcount=4](http://ubuntuforums.org/showpost.php?p=3783704&postcount=4)

---

