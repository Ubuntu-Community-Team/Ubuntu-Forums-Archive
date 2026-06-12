---
title: "Thunderbird gives SSL is disabled message after installing security updates yesterday"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by omega13a on 2010-04-10
I'm using Ubuntu 9.10 and yesterday, after installing some security updates that were related to Mozilla stuff, every time I check my email, I get this message about the SSL protocol being disabled and I can't get my email. I don't know what is wrong. I checked the advance configuration and security.enable_ssl3 is set to true though security.enable_ssl2 isn't (both are the default values). I don't know what is wrong. At one point I rebooted the computer and it didn't help. Any help will be greatly appreciated.

---

### Post by Cimmo on 2010-04-11
Same problem, didn't find a solution yet, this page didn't help too
[http://kb.mozillazine.org/SSL_is_disabled](http://kb.mozillazine.org/SSL_is_disabled)

---

### Post by Cimmo on 2010-04-11
I'm suspecting this update broke it
[http://changelogs.ubuntu.com/changelogs/pool/main/n/nss/nss_3.12.6-0ubuntu0.9.10.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/n/nss/nss_3.12.6-0ubuntu0.9.10.1/changelog)

---

### Post by Cimmo on 2010-04-11
yep
[https://bugs.launchpad.net/ubuntu/karmic/+source/nss/+bug/559881](https://bugs.launchpad.net/ubuntu/karmic/+source/nss/+bug/559881)

SOLUTION:
uninstall libnss3-0d and leave libnss3-1d

---

### Post by davidudin on 2010-04-11
Same problem, same circumstances. Removing libnss3-0d worked as advertised. Thanks.

---

### Post by mike.123850 on 2010-04-11
> **davidudin said:**
> Same problem, same circumstances. Removing libnss3-0d worked as advertised. Thanks.

Same for me, removing libnss3-0d worked.

Thank you,
Mike

---

### Post by ferch on 2010-11-19
# aptitude purge libnss3-0d

THANK YOU! 
Ubuntu 9.04

---

