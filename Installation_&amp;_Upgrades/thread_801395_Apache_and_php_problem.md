---
title: "Apache and php problem"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by m_kk on 2008-05-20
Hi,

I just upgraded from 7.07 to 8.04 hardy heron and it screwed everything up. When i try to execute a php script it says "dh_local(): Loading extensions is not permitted.". The apache2 does not start properly and httpd service is not available. When i tried to install httpd service by apt-get install httpd it give this message "You should explicitly select one to install.
E: Package httpd has no installation candidate". 

I have already uninstalled and installed apache2 and php5 several times. I regret my action Is there any way to roll back to 7.07?

---

### Post by tamoneya on 2008-05-20
httpd is a service not a package so apt-get wont work.  Try ```
sudo /etc/init.d/apache2 start
```Then try running the code.

There is no downgrade path from 8.04 to 7.10 so you must reinstall from scratch. Sorry.

---

