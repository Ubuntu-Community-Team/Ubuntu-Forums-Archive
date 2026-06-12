---
title: "OMSA service failed after updating the 12.04 kernel update to 3.13"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by t1819 on 2014-09-18
I updated my Ubuntu 12.04 with new kernel 3.13, After that dataeng service failed. Please help me out.

> service dataeng restart
Stopping Systems Management Data Engine:
Stopping dsm_sa_snmpd: Not started *
Stopping dsm_sa_eventmgrd: Not started *
Stopping dsm_sa_datamgrd: Not started *
Starting Systems Management Device Drivers:
Starting dell_rbu: Already started *
Starting ipmi driver: *


> service dataeng status
dsm_sa_datamgrd is stopped

---

### Post by mivok on 2014-10-23
> **t1819 said:**
> I updated my Ubuntu 12.04 with new kernel 3.13, After that dataeng service failed. Please help me out.

Not sure if you managed to solve this yet, but we've run into the same problem, and it looks like it's caused by the /etc/init.d/dm_sa_ipmi script (called by the dataeng service... eventually) trying to load the ipmi_msghandler module and failing to detect it loaded. This is because the module in question is now in the kernel and doesn't show up with lsmod that the script uses to detect if the module loaded ok.

Later versions of omsa (e.g. 7.4) correctly detect that the module is in the kernel. However, the apt repo changed from [http://linux.dell.com/repo/community/deb](http://linux.dell.com/repo/community/deb) to [http://linux.dell.com/repo/community/ubuntu](http://linux.dell.com/repo/community/ubuntu). If you go there it will give you instructions to upgrade and it should fix your issue.

---

