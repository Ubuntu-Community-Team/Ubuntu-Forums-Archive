---
title: "problem upgrading from Feisty to Gutsy"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by SourceV on 2007-10-13
While upgrading I have encountered with an error, so I ran: 'sudo dpkg --configure -a', which finish installing most of the packages, but ended with the following error:

Errors were encountered while processing:
 acpid
 docbook-xml
 acpi-support
 scrollkeeper
 powermanagement-interface
 doc-base
 kubuntu-desktop

Any suggestions?

---

### Post by louieb on 2007-10-13
I had similar problems with the upgrade to. But mine was on a test machine. So I just did a fresh install of Gutsy. BTW Gutsy doesn't automatically connect to the internet on reboot. Gutsy still has some bugs to work out.

---

### Post by Ferret-Simpson on 2007-10-13
The version-upgrade install method crashed right after downloading all packages
I installed them with update manager
Fixed the config issues like you did
Then reinstalled anything that seemed "borked"

---

