---
title: "How to install ssh tectia client on ubuntu?"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by randomlyrandom on 2009-12-19
Hi,

Is there a way to install ssh tectia client in ubuntu? If yes, how to install and where will this be installed? How to start this program?

---

### Post by Bachstelze on 2009-12-19
Probably not. What's wrong with OpenSSH?

---

### Post by NetTerm on 2012-06-01
The Tectia SSH client/server package is FIPS-140 certified, so that may be one reason a lot of commercial and government people may want to use that package.
 
Although Tectia does not currently support Ubuntu, it does work on Ubuntu 12.04. We tested using the Tectia 6.2.4.198 version.
 
We had a Tectia client/server installed on an old Redhat Enterprise 5.8 x86_64 system which we were removing from service. We decided to use the Ubuntu 12.04, x86_64 bit system as the replacement (great choice). All the Tectia related code is located in /etc/ssh2, /opt/tectia and the required ssh-server-g3 startup script in /etc/init.d so we just moved those directories and startup file to the Ubuntu system using sftp. Everything worked without change, including the ssh-server-g3 startup file. Both the client and server programs/utilites worked without any problems.
 
We then tried using Tectia client/server ssh X509 certificate authentication using a standard PIV smartcard and that also worked. All that was required was to install the OpenSC package to support the PIV smartcard/reader. This was done using the standard Ubuntu Software Center application.
 
Currently, Tectia is released in .rpm format for the Redhat x86_64 bit systems. I understand that Ubuntu has a package named alien that can be used to convert the .rpm format to .deb format so that may also be a way to install. However, we did not try that.

---

