---
title: "Problem with wrong version of python-minimal"
date: 2013-10-23
forum: Installation &amp; Upgrades
---

### Post by stephen16 on 2013-10-23
Hi,

When I try to install anything using the "apt-get install" command, I get the following error:
The following packages have unmet dependencies:
 python : Depends: python-minimal (= 2.7.3-0ubuntu2) but 2.7.3-0ubuntu2.2 is to be installed

Its a variant on a well-solved problem, but the package-manager appears to depend on Python, so I don't know if I can just remove python-minimal and replace it.

---

### Post by stephen16 on 2013-10-23
I just ran apt-get check. It says this:
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 python : Depends: python-minimal (= 2.7.3-0ubuntu2) but 2.7.3-0ubuntu2.2 is installed
E: Unmet dependencies. Try using -f.

Apparently I have version 2.2, and it wants to install the same version.

When running apt-get -f install, I get:
Setting up python-minimal (2.7.3-0ubuntu2.2) ...
dpkg: error processing python-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by stephen16 on 2013-10-23
Would it help anybody to figure this out if I noted that I only see this problem through the dpkg tool? Even the "python" command itself works.

---

