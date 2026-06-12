---
title: "Why no 'merge' option with config files in upgrade from 16.04 to 18.04 LTS?"
date: 2018-08-27
forum: Installation &amp; Upgrades
---

### Post by tcn2 on 2018-08-27
This afternoon I ran the upgrade from 16.04 LTS to 18.04 LTS on my network gateway machine. I was distracted during the upgrade procedure or I would have been smarter, but for three config files (sysctl.conf, named.conf and dhcpd.conf) I was prompted to keep or replace my local copies.
The upgrade procedure allows the user to see a diff (and on the basis of the diff I updated sysctl.conf and kept the other two files), but it does not allow the user to merge their local changes into the new file, which would have been a useful option I think.
Because overwriting the named and dhcpd configs would have led to a great deal of inconvenience I chose to keep them but I would now like to review the distro files and possibly edit my local copies. At least with sysctl.conf I can refer to my backups, but where does the upgrade process put the proffered versions of the config files when the user opts not to replace them?

cheers
T

---

### Post by deadflowr on 2018-08-27
> but where does the upgrade process put the proffered versions of the config files when the user opts not to replace them?

If anywhere, look in /usr/share/doc
usually in an examples sub-folder for whatever package/program the config file is for.
sysctl.conf should be the procps folder, fwiw.
I Don't know where the other are. I guess named.conf would be in bind9 and dhcpd.conf would be whatever dhcpd package you installed.

---

