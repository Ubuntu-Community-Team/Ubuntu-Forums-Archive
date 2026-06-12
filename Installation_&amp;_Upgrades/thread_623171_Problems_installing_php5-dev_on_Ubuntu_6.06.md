---
title: "Problems installing php5-dev on Ubuntu 6.06"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by harunahi on 2007-11-25
Hi,

I seem to need phpize in order to install PDO. I believe the best way to get this is to install php5-dev. However, this doesn't seem to work for me. Can anyone please help? See below:

----
root@ubuntu:/# apt-get install php5-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  php5-dev: Depends: autoconf but it is not installable
            Depends: automake1.4 but it is not installable
            Depends: libssl-dev but it is not going to be installed
            Depends: libtool but it is not installable
            Depends: shtool but it is not installable
E: Broken packages
----

What do I do now? How can I get around this?
Thanks for any help!

---

### Post by harunahi on 2007-11-27
Doh!

apt-get update

Sorted.

---

