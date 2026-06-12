---
title: "Scanner Driver Installation"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by rsvasan72 on 2007-07-15
Hi,
I was trying to install a scanner (Brother DCP-7020) and I installed a wrong driver. I tried to uninstall it with SPM, it gave me the following Error "E: brscan2: subprocess post-removal script returned error exit status 1" Then I edited the file "brscan2.postrm" located in the directory "/var/lib/dpkg/info" by appending the command 'exit 0' behind the first line. Now it gives me ""E: brscan2: subprocess post-removal script returned error exit status 2" I could not uninstall it anymore. I would appreciate any help to resolve this issue.
Thanks
Srini

---

