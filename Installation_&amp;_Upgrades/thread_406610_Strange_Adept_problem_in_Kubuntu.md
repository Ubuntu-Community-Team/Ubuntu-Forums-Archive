---
title: "Strange Adept problem in Kubuntu"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by gordebak on 2007-04-11
I use Kubuntu Feisty. I tried to remove some packages related to kubuntu-desktop dummy package, and of course adept wanted to remove everything. I canceled the operation immediately. But now on when I start Adept Manager it says,

> You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

But actually I don't have anything running. Any help appreciated. Do I have to reinstall the system?

EDIT: After running the following command it is ok now.

> sudo dpkg --configure -a

---

### Post by PhilF on 2007-04-11
Thanks for this - I had pretty much the same problem because I had not read the installation instructions on the jdk-6-doc package properly.  When adept tried to install it it errored with a dialog box.  Once OK'd the process stopped dead and I didn't realise that this was still sitting in the background!

Cheers!:D

---

