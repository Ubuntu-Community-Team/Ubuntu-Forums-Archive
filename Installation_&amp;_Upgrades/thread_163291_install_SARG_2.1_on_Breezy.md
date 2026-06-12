---
title: "install SARG 2.1 on Breezy?"
date: 2006-04-20
forum: Installation &amp; Upgrades
---

### Post by pixel80r on 2006-04-20
Does anyone know of a repository where I can get SARG 2.1 for breezy.
the standard repositories only show version 1.0.8 and unfortuniately it has some bugs that prevent proper reporting.

If not, how can I go back to version 1.0.5?

BTW, This is a Server install with no X installation.

thanks.

---

### Post by pixel80r on 2006-04-25
Anyone??

---

### Post by Jagot on 2006-04-25
[http://rpm.rutgers.edu/repository/ubuntu/pool/universe/s/sarg/](http://rpm.rutgers.edu/repository/ubuntu/pool/universe/s/sarg/)

There appears to be 2.1-2 on the above site.

You should be able to wget and sudo dpkg -i it.

Alternatively there are packages made specifically for Debian which may work with Ubuntu but use them at your own risk:

[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=sarg](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=sarg)

Hope that's what you're looking for.

---

### Post by pixel80r on 2006-04-25
Thanks Jagot.
Is the dpkg method easily managed if I want to later use an "official" version that might be available through apt in the future. Will there be any conflicts?

---

### Post by Jagot on 2006-04-25
It should be ok.  You can remove the package using dpkg -P then apt-get install the official one.

I wouldn't have thought there should be any conflicts but to be honest I can't say for sure.  Someone else may be able to fill you in on that one.

---

### Post by pixel80r on 2006-05-03
Thanks again Jagot.
I used wget and dpkg to install the newer version of sarg and it works great.

Now if I can only get squid to authenticate againt Active Directory....

---

