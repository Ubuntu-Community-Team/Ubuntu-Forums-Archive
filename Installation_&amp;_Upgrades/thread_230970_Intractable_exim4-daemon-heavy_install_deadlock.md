---
title: "Intractable exim4-daemon-heavy install deadlock"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by MaskedMarauder on 2006-08-06
I'm trying to upgrade from Breezy >>--> Dapper.  Almost everything went OK, but I'm stuck with the following problem that I can't work around:

it refuses to upgrade, install or remove exim4-daemon-heavy.  I can't get around it. 

I upgraded another breezy to dapper and it went ok. For some obscure reason it used postfix instead of exim4 and there were no problems.  On this machine I can't install postfix over the broken exim4 and I can't fix exim4 or remove exim4 to allow postfix to install.  Despite the hopeful error message exim4 won't install, deinstall, reinstall, or anything.

Here's the error message I get:

root: apt-get -y install postfix
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre
Recommended packages:
  resolvconf
The following packages will be REMOVED:
  exim4-config exim4-daemon-heavy
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 2 to remove and 404 not upgraded.
1 not fully installed or removed.
Need to get 0B/923kB of archives.
After unpacking 344kB of additional disk space will be used.
dpkg: error processing exim4-daemon-heavy (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Abort


------------------------------

How do I kill this M-Fer?  Do I need garlic, wooden stakes, crucifixes and silver bullets?  Or is there an easier way short burning a CD and installing anew on top of my existing data?

---

