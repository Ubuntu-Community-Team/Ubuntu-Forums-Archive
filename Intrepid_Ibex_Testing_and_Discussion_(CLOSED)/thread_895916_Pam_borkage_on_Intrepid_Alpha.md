---
title: "Pam borkage on Intrepid Alpha"
date: 2008-08-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jaem on 2008-08-20
Hey all,

I've been running Intrepid Desktop 64-bit since shortly after Alpha 3 was released, and aside from the first couple of days, I haven't had any issues.  (Disclaimer: yes, I read the "do not install on production machines" warning, but I like to live on the edge.)
About half an hour ago, I powered down my computer.  I had just installed updates a few minutes prior to that, including some of the PAM libs.  I hadn't touched any settings related to users or authentication during that session.  When I rebooted and tried to login, GDM gave me an "Authentication Failed" pop-up, and console loging similarly failed.  I rebooted into a recovery shell and examined the logs; I found this:
```
pam_nologin(gdm:auth): cannot determine username
pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=foo
FAILED LOGIN (1) on 'tty1' FOR `foo', Authentication failure
FooBar login[5903]: Cannot make/remove an entry for the specified session
FooBar login[6102]: Cannot make/remove an entry for the specified session
```
I suppose this is still speculation, but the circumstances make me think that the PAM update may have been the cause.  I'll take a further look into it, but if anyone more learned in such things wants to check it out, that would be appreciated.  If anyone else has had this problem after updating today, and has anything to add (e.g. not just an endless list of "me too"s), please do.

---

### Post by sdennie on 2008-08-20
Moved to Intrepid forum where it's more likely to be seen.

---

### Post by jaem on 2008-08-20
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/259867](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/259867)
Apparently it's fixed.  Quick work!

---

