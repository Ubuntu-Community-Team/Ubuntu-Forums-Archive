---
title: "Errors when trying to remove/install Samba"
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by shrybouski on 2012-06-20
I am having a problem with Samba package. So I did the following to remove it, and got some errors.
  "# sudo apt-get --purge remove samba-common Reading package lists... Done Building dependency tree
Reading state information... Done The following packages will be REMOVED:   samba* samba-common* samba-common-bin* 0 upgraded, 0 newly installed, 3 to remove and 6 not upgraded. 4 not fully installed or removed. After this operation, 42.4 MB disk space will be freed. Do you want to continue [Y/n]? Y (Reading database ... 195751 files and directories currently installed.) Removing samba ... Purging configuration files for samba ... Removing configuration file /etc/default/samba... Removing configuration file /etc/default/samba... Removing samba-common-bin ... Removing samba-common ... Purging configuration files for samba-common ... **perl: error while loading shared libraries: libperl.so.5.12: cannot open shared object file: No such file or directory dpkg: error processing samba-common (--purge):  subprocess installed post-removal script returned error exit status 127 Processing triggers for man-db ... perl: error while loading shared libraries: libperl.so.5.12: cannot open shared object file: No such file or directory Processing triggers for ureadahead ... Processing triggers for ufw ... Errors were encountered while processing:  samba-common** E: Sub-process /usr/bin/dpkg returned an error code (1)"


All these errors seem to be linked to**libperl.so.5.12 ** and appeared after distro upgrade to 12.04 [B]. 
[/B]

Any ideas?

---

