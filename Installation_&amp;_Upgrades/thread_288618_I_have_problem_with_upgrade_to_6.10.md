---
title: "I have problem with upgrade to 6.10"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by igorzolnikov on 2006-10-30
My PC rebooted in process upgrade to 6.10 and didn't start X.

I tried sudo apt-get upgrade and sudo apt-get dist-upgrade.

Now i have following problem:

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  ant python-adns python-clientcookie python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-htmlgen python-imaging python-imaging-sane python-jabber python-ldap
  python-pam python-pexpect python-pylibacl python-pyopenssl python-pyxattr
  python-reportlab python-simpletal python-sqlite python-xmpp
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up acpid (1.0.4-5ubuntu4) ...
 * Loading ACPI modules...                                               [ ok ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
E: Sub-process /usr/bin/dpkg returned an error code (1)


I can't upgrade 21 packages.

Plz, help me.

---

### Post by igorzolnikov on 2006-10-30
My PC have rebooted in process upgrade to 6.10.

X didn't start.

I tried "sudo apt-get upgrade" and "sudo apt-get dist-upgrade" in console.

X have started, but now i have following problem:

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
ant python-adns python-clientcookie python-egenix-mxproxy
python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
python-htmlgen python-imaging python-imaging-sane python-jabber python-ldap
python-pam python-pexpect python-pylibacl python-pyopenssl python-pyxattr
python-reportlab python-simpletal python-sqlite python-xmpp
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up acpid (1.0.4-5ubuntu4) ...
* Loading ACPI modules... [ ok ]
* Starting ACPI services... invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
acpid
acpi-support
E: Sub-process /usr/bin/dpkg returned an error code (1)


I can't upgrade 21 packages.

Plz, help me.

---

