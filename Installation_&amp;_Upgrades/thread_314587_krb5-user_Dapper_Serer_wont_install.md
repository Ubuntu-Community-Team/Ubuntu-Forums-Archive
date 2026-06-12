---
title: "krb5-user Dapper Serer wont install"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by acgiglyph on 2006-12-07
In trying to follow the FAQ [here]("http://ubuntuforums.org/showthread.php?t=91510&highlight=active+Directory") on joining a Microsoft Active Directory, the tutorial has you install kerbos.  

When I enter 
sudo apt-get install krb5-user
I get:
> Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  krb5-user: Depends: krb5-config but it is not installable
E: Broken packages

when I try to install krb5-config I get:
> Reading package lists... Done
Building dependency tree... Done
Package krb5-config is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package krb5-config has no installation candidate

My sources for apt are:
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

can anyone help me as to why I cant install this package?> 

---

### Post by acgiglyph on 2006-12-07
The solution is to modify the sorce list from
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted 

to
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

Note that these are the ones at the TOP of the page not the bottom of the page.

---

