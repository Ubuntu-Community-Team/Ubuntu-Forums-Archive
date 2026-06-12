---
title: "[SOLVED] Update error"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by haneya on 2008-06-20
when i press update button i got this
 ```

W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://jo.archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://jo.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```


and i cant update my system ](*,)

i am using ubuntu 8.04

---

### Post by avtolle on 2008-06-20
Try selecting the main mirror in software sources (System>>Administration>>Software Sources, enter your password, then on the first page, change download from bar to either Main Server or United States server (or something close to that), reload when prompted, then after everything is updated, close out software sources (if it doesn't automatically close). Then, try it again.

---

### Post by haneya on 2008-06-20
thx dude it works now i turned it to the main server :)

---

