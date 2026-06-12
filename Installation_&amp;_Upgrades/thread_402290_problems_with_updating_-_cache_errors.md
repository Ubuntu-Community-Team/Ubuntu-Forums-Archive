---
title: "problems with updating - cache errors"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by neill on 2007-04-05
when i run sudo apt-get upgrade i get the following error

**********************************************************

Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libkrb53 1.4.3-5ubuntu0.3 [425kB]
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libfreetype6 2.1.10-1ubuntu2.3 [440kB]
Fetched 865kB in 3s (283kB/s)
(Reading database ... 77309 files and directories currently installed.)
Preparing to replace libkrb53 1.4.3-5ubuntu0.2 (using .../libkrb53_1.4.3-5ubuntu0.3_amd64.deb) ...
Unpacking replacement libkrb53 ...
dpkg (subprocess): unable to execute old post-removal script: Permission denied
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error processing /var/cache/apt/archives/libkrb53_1.4.3-5ubuntu0.3_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace libfreetype6 2.1.10-1ubuntu2.2 (using .../libfreetype6_2.1.10-1ubuntu2.3_amd64.deb) ...
Unpacking replacement libfreetype6 ...
dpkg (subprocess): unable to execute old post-removal script: Permission denied
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error processing /var/cache/apt/archives/libfreetype6_2.1.10-1ubuntu2.3_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libkrb53_1.4.3-5ubuntu0.3_amd64.deb
 /var/cache/apt/archives/libfreetype6_2.1.10-1ubuntu2.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

 ***********************************************************************************

this means utterly nothing to me :confused: 

can anyone help ??

thanks

neill

---

### Post by zvacet on 2007-04-07
I´m not promissing anything but try this
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by neill on 2007-04-09
fixed it - by accident !!

i'd made some 'security enhancements' to /etc/fstab so /var was now mounted as noexec, nosuid and nodev (as i recall)

when i changed them all back to defaults - ta da - it worked :) 

thanks for the help anyway

neill

---

