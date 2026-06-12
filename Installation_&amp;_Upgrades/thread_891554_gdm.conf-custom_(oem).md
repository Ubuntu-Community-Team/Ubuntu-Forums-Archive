---
title: "gdm.conf-custom (oem)"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by Loaded.len on 2008-08-16
Anybody know what goes on in /etc/gdm when you prepare an OEM install for shipping? 

Here's the deal.  I used reconstructor to create a new live desktop CD... among other things (like changing the themes and whatnot, I also added the following into my /etc/gdm/PostLogin/Default

```
cat /etc/gdm/gdm.conf-custom | sed s/Automaticlogin=.*/AutomaticLogin=$LOGNAME/ > /etc/gdm/gdm.conf-placeholder && mv /etc/gdm/gdm.conf-placeholder /etc/gdm/gdm.conf-custom
```

That may appear to be ugly to you gurus, and I'm aware of the security risks, but what it does for me is lets the last known user automatically login, until they manually logout, then subsequent logins from any user are set to automatically login.

During an OEM setup, there are multiple gdm.conf-xxxx files.  (gdm.conf.oem, gdm.conf-custom, gdm.conf-custom.orig) When oem-config runs, how does it re-arrange those files?  As it is right now, the gdm.conf-custom file doesn't have AutomaticLogin entries under [daemon], just wondering if I need to mess around more before I waste a bunch of time building ISO's.

---

