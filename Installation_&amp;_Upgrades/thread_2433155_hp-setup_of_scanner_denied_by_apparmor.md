---
title: "hp-setup of scanner denied by apparmor"
date: 2019-12-14
forum: Installation &amp; Upgrades
---

### Post by pr0llux on 2019-12-14
My HP mfc worked fine under 19.04.  Since upgrading to 19.10 it prints fine, but isn't detected as a scanner.  
When I run hp-setup I get apparmor denied messages like:
  
    audit: type=1400 audit(1576356403.647:206): apparmor="DENIED" operation="open" profile="/usr/share/hplip/setup.py" name="/opt/OpenPrinting-Gutenprint/sbin/" pid=10142 comm="python" requested_mask="r" denied_mask="r" fsuid=1001 ouid=0
Anybody got any hints?
Thanks
Richard

---

