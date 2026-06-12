---
title: "Unable to download/install 3 security updates"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by udstudent on 2007-11-16
Hi,

I received an automatic message to download/install 3 new security updates but keep getting and error message when I try to "install now".  I am using Edge Eft.  The errors are:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.22-1ubuntu4.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.22-1ubuntu4.3_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.22-1ubuntu4.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.22-1ubuntu4.3_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.22-1ubuntu4.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.22-1ubuntu4.3_i386.deb)
  403 Forbidden


Any help would be appreciated.

---

### Post by stephen53 on 2007-11-16
I got the same error running Dapper Drake. I did a google search and found out that this is a server error which means for some reason the connection was refused. Hopefully what ever the problem was the administrator of the server will fix the problem. It could be that the server was down for maintenance or overwhelm with requests. I am going to try later and see if I can get the updates.

---

### Post by zzatz on 2007-11-16
Launchpad indicates that there is a problem with the update, so access has been disabled. A fixed version is being worked on and should be available soon.

In other words, try again later ;)

---

### Post by dast on 2007-11-16
I can confirm the same behavior here with the same updates, current as of the time of this post...  Still 403'ing.  Sounds like people are already aware of the problem, so I suppose we should all just try again later today...?   :)

---

### Post by kamikazi on 2007-11-16
I got the same problem too, seem like there are some problems with the upgrade server.
Hope their will fix this soon. :(

---

### Post by ptn107 on 2007-11-16
Behavior confirmed on gutsy-64

---

### Post by Neobuntu on 2007-11-16
Same problem here.

Any ETA on a fix?

---

### Post by mandrill on 2007-11-16
The very same.

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden

---

### Post by jdong on 2007-11-16
See [http://ubuntuforums.org/showpost.php?p=3783704&postcount=4](http://ubuntuforums.org/showpost.php?p=3783704&postcount=4)

---

### Post by lavinog on 2007-11-16
Thank you for confirming this...I was getting concerned it was my setup

---

### Post by jdong on 2007-11-16
Sure thing; I'm gonna close this thread to keep all discussion in a central place.

Please see [http://ubuntuforums.org/showthread.php?t=463944](http://ubuntuforums.org/showthread.php?t=463944) to continue discussion

---

