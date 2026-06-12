---
title: "Upgrading Ubuntu from 14.04 to 14.04.1"
date: 2014-07-26
forum: Installation &amp; Upgrades
---

### Post by nikhilbhalwankar on 2014-07-26
Hi,

I would ike to upgrade my desktop running Ubuntu 14.04 to 14.04.1. Please let me know the procedure for the same. I tried google search but could not find any relevant links.

---

### Post by Dennis N on 2014-07-26
If you have been doing the regular updates, then you probably have 14.04.1 already through those updates. 

Check as follows: Mine shows 14.04.1 LTS and I have only done regular updates
```
dmn@Roxanne:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty
```

Nothing more to be done.

---

### Post by Jessie_James_A._At on 2014-07-26
i got mine too in software updates

```
lsb_release -a && uname -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
Linux xsoultribex-Aspire-V3-571G 3.15.0-031500-generic #201406131105 SMP Fri Jun 13 15:06:46 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by nikhilbhalwankar on 2014-08-01
> **Dennis N said:**
> If you have been doing the regular updates, then you probably have 14.04.1 already through those updates. 

Check as follows: Mine shows 14.04.1 LTS and I have only done regular updates
```
dmn@Roxanne:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

Nothing more to be done.


Thanks a lot for this. Mine too is 14.04.1 LTS. Looks like regular updates have done the work.

nikhil@nikhil-Inspiron-N5010:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
nikhil@nikhil-Inspiron-N5010:~$

---

