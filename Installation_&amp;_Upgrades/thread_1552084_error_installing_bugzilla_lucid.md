---
title: "error installing bugzilla lucid"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by Cfossy2 on 2010-08-13
When I iried to install bugzilla on my Ubuntu Lucid, I kept getting the following message. I have used "sudo apt-get --configure -a " and this is as far as I can get with the installation. Is there a way of first stopping the process and then removing Bugzilla, as it has locked the admin for apt.



Setting up bugzilla3 (3.2.5.1-2) ...
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla3.conf
granting access to database bugzilla3 for bugzilla3@localhost: already exists.
creating database bugzilla3: already exists.
dbconfig-common: flushing administrative password
revoking access to database bugzilla3 from bugzilla3@localhost: success.
granting access to database bugzilla3 for bugzilla3@localhost: success.
verifying access for bugzilla3@localhost: success.
run-parts --exit-on-error --lsbsysinit /etc/bugzilla3/pre-checksetup.d
run-parts: executing /etc/bugzilla3/pre-checksetup.d/10fixcompiledtemplates
run-parts: executing /etc/bugzilla3/pre-checksetup.d/30copyetcskins
run-parts: executing /etc/bugzilla3/pre-checksetup.d/30copyetctemplate
run-parts: executing /etc/bugzilla3/pre-checksetup.d/50patchtemplatefordebian


Regards,
Cfossy:popcorn:

---

### Post by tishaton on 2011-01-07
Hi,

Cfossy:To cancel it, simply Control+C and "sudo apt-get purge bugzilla3"

Got the same problem: freeze during the installation... Any solution yet ? (in order to perform the installation, i mean)

for info: uname -a give:
Linux xxx 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux

regards,

Tishaton

---

### Post by sikander3786 on 2011-01-07
> **tishaton said:**
> Hi,

Cfossy:To cancel it, simply Control+C and "sudo apt-get purge bugzilla3"

Got the same problem: freeze during the installation... Any solution yet ? (in order to perform the installation, i mean)

for info: uname -a give:
Linux xxx 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux

regards,

Tishaton
Welcome to the forums :-)

I couldn't exactly understand if you are getting any problems.

Please post the output of following command to let us see the problem.

Applications > Accessories > Terminal:
```
sudo dpkg --configure -a
```

---

