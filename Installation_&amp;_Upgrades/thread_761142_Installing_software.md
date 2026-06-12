---
title: "Installing software"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by Shakeysteve on 2008-04-20
How do I install Thunderbird after downloading the .tar.gz file?

---

### Post by unutbu on 2008-04-20
Are you sure you want to install from the .tar.gz?
The easiest way is to use apt-get:

```
sudo apt-get install thunderbird
```

---

### Post by Shakeysteve on 2008-04-20
Apt get gives the buggy 1.5 version. I need 2.0.0.12 version.

---

### Post by unutbu on 2008-04-20
Are you using gutsy? Because the 2.0.0.12 version is available in gutsy-updates.

```
% apt-cache policy thunderbird
thunderbird:
  Installed: (none)
  Candidate: 2.0.0.12+nobinonly-0ubuntu0.7.10.0
  Version table:
     2.0.0.12+nobinonly-0ubuntu0.7.10.0 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
     2.0.0.6+nobinonly-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
```

---

### Post by Chilongola on 2008-04-21
Try these:
[http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/](http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/)

[http://www.cyberciti.biz/faq/install-thunderbird-2-in-linux/](http://www.cyberciti.biz/faq/install-thunderbird-2-in-linux/)

---

### Post by Shakeysteve on 2008-04-21
[http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/](http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/)

worked fairly well thanks! Just one issue.
To save all emails & addresses I read in Mozilla support to copy the profiles folder elsewhere as a backup, but the new install would pick up the old profile. This didn't happen. How do I incorporate the old saved profile into the new one?

Thanks for your help,
Steve.

---

