---
title: "installer does not let me use user name &quot;admin&quot;"
date: 2020-07-31
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2020-07-31
i want to have user name "admin" be the system administrator (initially the only user, thus the only user sudo will allow).  but the *ubuntu installer, as of a few recent versions, won't let me enter that name.  is there a reason why not?  my workaround has been to create a different name, such as "adminx" and change its user name and home directory path, later.

---

### Post by Tadaen_Sylvermane on 2020-07-31
I don't know why that is. I've never used that for a username before. Maybe it's already used. If that is the case maybe make a user with sudo, login, and adjust that user to be able to login? May be a bad idea. Without knowing why it's blocked you may run into issues.

---

### Post by grahammechanical on 2020-07-31
My guess would be that the installer is set up to accept a user name for a standard user and "admin" might be blacklisted as a standard user name. 

After installation it is possible to use System Settings>Details to add a user and mark that user as either a standard user or administrator user with its own password. It might be possible in this way to set up a generic name for the administrator that can be used by the person tasked as administrator.

Those who have experience maintaining several machines might have better advice on how to setup non-personal user names and passwords that many employees can use while also having a non-personal administrator account to give access to all machines.

Regards.

P.S. I have just seen a man page that makes it clear that "admin" is a group. The user names that have sudo privileges are put in a group called "admin."

[http://manpages.ubuntu.com/manpages/trusty/man8/sudo_root.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/sudo_root.8.html)

I guess we cannot have a standard user with the name of the admin group.

---

### Post by CatKiller on 2020-07-31
> **grahammechanical said:**
> I guess we cannot have a standard user with the name of the admin group.

Exactly so. The user gets a group of the same name, and *admin* is already taken. You'd probably also cause yourself problems by trying to call your user "cdrom," "plugdev," or "sambashare."

---

### Post by pbear42 on 2020-08-01
In my understanding, one of the reasons Ubuntu stopped setting a root password was to make it more difficult to hack into the system from a remote location, as the hacker has to guess two pieces of information (username and password) rather than only the password. (Ironically, this makes hacking with physical access easier, but that's always been vulnerable.)  So, my SWAG about this question would be more of the same, i.e., a view that *admin* is easy to guess and, thus, a security risk.

---

### Post by GhX6GZMB on 2020-08-01
Yep, "admin" is already taken (by the system) and can't be reused. Apart from that, I find it an exceptionally bad idea to use names that already have a system relevance. It will lead to endless confusion in the future.

---

### Post by Skaperen on 2020-08-06
i did create a user named "admin" after the system was installed and my addons were put in (it let me then).  i used "adminx" (where "x" was some other letter) to do the install.  i'm guessing i should avoid doing that for my 20.04 system i am still planning (got delayed back in April and May).  this cycle will be more of an effort since i need to resize partitions and this involves reformatting and restoring /home as part of this.

---

