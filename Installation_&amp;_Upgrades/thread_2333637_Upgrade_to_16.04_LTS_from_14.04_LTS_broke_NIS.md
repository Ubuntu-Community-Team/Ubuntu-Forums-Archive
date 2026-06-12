---
title: "Upgrade to 16.04 LTS from 14.04 LTS broke NIS"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by toddpedlar on 2016-08-11
I searched the forums and was unable to come up with anything like what I've experienced today.  

I have a set of servers and four desktops for a research lab, all running Ubuntu 14.04 LTS currently.  I was beginning an upgrade to the OS and started with a pair of the desktops, which happily upgraded to 16.04 LTS... happily, except that upon rebooting, they became "unclustered".  That is, they will not bind to the NIS server in the cluster, and therefore no user accounts are enabled.  NFS is not broken - the /home/user area that's served by the NFS server in the cluster is still happy having its disk crossmounted on these two machines, but no users are known to the desktops now because of the broken NIS.

Is this a known problem?  What might be suggested as a fix?

Thanks,

Todd

---

### Post by toddpedlar on 2016-08-11
If the answer is "just migrate to LDAP" then I suppose I have the time to do that.   Is there a good NIS-to-LDAP migration guide for taking existing clusters from NIS authentication to LDAP?  I have seen some very old documentation for this, but nothing very recent.  Any pointers would be appreciated.

Thanks,

Todd

---

