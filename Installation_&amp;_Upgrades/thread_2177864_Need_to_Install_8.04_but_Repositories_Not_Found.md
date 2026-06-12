---
title: "Need to Install 8.04 but Repositories Not Found"
date: 2013-09-30
forum: Installation &amp; Upgrades
---

### Post by NorthWill on 2013-09-30
I have a need to install a copy of Ubuntu 8.04 because we had a server crash and with the particular software that server was running, I need to rebuild exactly the same environment in order to restore from backup before I migrate to a new (supported) environment. 

I have installed 8.04 (32 bit) but any attempt to install packages or do an apt-get update gives me a series of 404 Not Found errors.  I'm assuming that the repositories listed in /etc/apt/source.list are no longer valid.  Can anyone point me to where I can find those repositories?

```
Err http://security.ubuntu.com hardy-security/main Packages
  404 Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com hardy-security/restricted Packages
  404 Not Found [IP: 91.189.92.184 80]
Err http://ca.archive.ubuntu.com hardy/main Packages
  404 Not Found [IP: 91.189.92.156 80]
Err http://ca.archive.ubuntu.com hardy/restricted Packages
  404 Not Found [IP: 91.189.92.156 80]
Err http://security.ubuntu.com hardy-security/main Sources
  404 Not Found [IP: 91.189.92.184 80]
Err http://ca.archive.ubuntu.com hardy/main Sources
  404 Not Found [IP: 91.189.92.156 80]
Err http://ca.archive.ubuntu.com hardy/restricted Sources
  404 Not Found [IP: 91.189.92.156 80]
Err http://security.ubuntu.com hardy-security/restricted Sources
  404 Not Found [IP: 91.189.92.184 80]
and so on ...

```

Thanks,

---

### Post by westie457 on 2013-09-30
Hello NorthWill. Welcome to UF.

This link might be of some help to you. [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)

---

### Post by brad6 on 2013-09-30
Thank you.  That seems to be precisely what I needed.

---

### Post by brad6 on 2013-09-30
Thank you.  That seems to be precisely what I needed.

---

