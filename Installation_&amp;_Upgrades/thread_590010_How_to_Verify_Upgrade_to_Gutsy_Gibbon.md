---
title: "How to Verify Upgrade to Gutsy Gibbon?"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by TechieZero on 2007-10-24
After you *think* you have upgraded to GG, how can you verify it properly?

I am using Kubuntu and I am linux n00b.

---

### Post by #!/bin/bash on 2007-10-24
cat /etc/issue
That should show the version:

---

### Post by Route490 on 2007-10-24
Another way if the above doesn't work =)


sudo lsb_release -a

you should see something like this:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy


Enjoi

---

### Post by TechieZero on 2007-10-25
That worked great. Thanks. :popcorn:

---

