---
title: "Unmet dependencies. How to downgrade a package?"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by dazz100 on 2012-10-09
Hello

I am trying to install dchp3 server but I have hit a problem with unmet dependancies.  It appears that I have a later version isc-dhcp-common than Unbuntu 12.04 expects.  I don't know how to downgrade to the earlier version to fix this problem.

apt-get doesn't seem to be able to cope with this problem.

```

dazz@toshiba:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-26-generic linux-headers-3.2.0-26 linux-headers-3.2.0-26-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  isc-dhcp-server
Suggested packages:
  isc-dhcp-server-ldap
The following packages will be upgraded:
  isc-dhcp-server
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/427 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of isc-dhcp-server:
 isc-dhcp-server depends on isc-dhcp-common (= 4.1.ESV-R4-0ubuntu5.2); however:
  Version of isc-dhcp-common on system is 4.1.ESV-R4-0ubuntu5.5.
dpkg: error processing isc-dhcp-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 isc-dhcp-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bart.a on 2012-10-09
Have you tried removing the package and reïnstalling the "older" package?
Note that I do not know what removing/downgrading the package will do to your current configuration.

**First, check available versions you can install:**

apt-cache showpkg *packagename*

**Install the version you need:**

sudo apt-get install *packagename=version*

**Prevent auto updating the package to the newer version. Remind yourself that you are holding this version. You will be able to upgrade it eventualy:**

sudo echo “*package* hold” | sudo dpkg –set-selections

---

### Post by dazz100 on 2012-10-11
Hi

Unfortunately non of those commands worked.  Nothing I do seems to budge the wrong version.  apt-get doesn't seem to be able to fix this problem.

I have tried commands on isc-dhcp-server  and dhcp3-server but no progress.

Still stuck.

Regards


Dazz

---

### Post by dazz100 on 2012-10-11
Hi

I think the answer is here:
[http://forums.hak5.org/index.php?/topic/26455-dhcp3-server/](http://forums.hak5.org/index.php?/topic/26455-dhcp3-server/)
using Synaptic to force the lower version.  
I then uninstalled dhcp3-server and reinstalled.

I got different error messages that I think just say dhcp3 needs to be configured.  I need to do some further testing.

Dazz

---

### Post by bart.a on 2012-10-11
using synaptic is the graphical way of going about things.. basically it's doing the same..

You have removed the old and installed a new version, so it needing configuration is possible..

---

### Post by dazz100 on 2012-10-12
Hi
The difference between synaptic and apt-get is that synaptic solved this problem and apt-get didn't.

I am now trying to configure isc-dhcp-server.  The unmet dependancies problem has gone.

Dazz

---

### Post by bart.a on 2012-10-12
you're right! it did.. that is a big difference :lolflag:

---

