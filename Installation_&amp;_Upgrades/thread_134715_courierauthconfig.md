---
title: "courierauthconfig"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by changewand on 2006-02-22
Hya! I'm trying to install functionality that will allow my webmail users to change their passwords. When I tried to run the configure script for courierpassd, it gave me the following error:

configure: WARNING: === Courier authentication library not found.
configure: WARNING: === You need to download and install
configure: WARNING: === [http://www.courier-mta.org/download.php#authlib](http://www.courier-mta.org/download.php#authlib) first.
configure: WARNING: === If courier-authlib is installed in a non-default
configure: WARNING: === directory, set the COURIERAUTHCONFIG environment
configure: WARNING: === variable to the full path to the courierauthconfig
configure: WARNING: === binary and rerun this configure script.
configure: WARNING:
configure: error: courierauthconfig not found

two questions:
1) is there a package for courierpassd?
2) is there a package for courier-authlib? or do I have to install the tarballs for both?

Also, if there's another way to allow for password changing from squirrelmail, I'd love to hear it!

Brandon

---

