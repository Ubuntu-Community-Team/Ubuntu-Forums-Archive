---
title: "archive.canonical.com malfunctioning?"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by ThomasNovin on 2007-06-04
Kind of hard to say what forum this should be in, but I'm trying to install/upgrade vmware-server but the main deb package cannot be downloaded, I suspect something is wrong with [http://archive.canonical.com](http://archive.canonical.com)

/var/cache/apt/archives$ s wget [http://archive.canonical.com/ubuntu/pool/main/v/vmware-server/vmware-server_1.0.3-1_i386.deb](http://archive.canonical.com/ubuntu/pool/main/v/vmware-server/vmware-server_1.0.3-1_i386.deb)
--15:58:50--  [http://archive.canonical.com/ubuntu/pool/main/v/vmware-server/vmware-server_1.0.3-1_i386.deb](http://archive.canonical.com/ubuntu/pool/main/v/vmware-server/vmware-server_1.0.3-1_i386.deb)
           => `vmware-server_1.0.3-1_i386.deb'
Resolving archive.canonical.com... 82.211.81.142
Connecting to archive.canonical.com|82.211.81.142|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 79,434,866 (76M) [application/x-debian-package]

 0% [                                                                   ] 425,368       --.--K/s  ETA 3:44:44

<Timeout>

---

### Post by ThomasNovin on 2007-06-04
Works now again. case closed (was "down" for 10-15 minutes)

---

