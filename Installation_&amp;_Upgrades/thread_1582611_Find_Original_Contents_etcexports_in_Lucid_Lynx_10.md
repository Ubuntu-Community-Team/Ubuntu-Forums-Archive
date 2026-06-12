---
title: "Find Original Contents /etc/exports in Lucid Lynx 10.04?"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by tnoell on 2010-09-26
So I upgraded to Lucid Lynx 10.04 ... during the upgrade, it asked me if I wanted to keep my modified /etc/exports file.  There were a couple of new entires in the /etc/esports file from 10.04 that I did not have, but I did not note what they were.  So I selected "open a shell to inspect" (or similar) and it opened a shell, then I simply made a copy of my existing /etc/exports file.

After I exited the shell, it continued the installation as though I had some how resolved the conflict (I had not).  Now the /etc/exports file is my original, and I do not recall what the additional lines that were in the /etc/exports from the 10.04 upgrade.

When I run dpgs -S /etc/exports, it tells me no package provides this file.

So, where can I get the original contents of the 10.04 /etc/exports so I can see the new lines and determine if I need them or not?

Here is the current contents of my /etc/esports:


# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/export       192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/users 192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)


What ever lines 10.04 wanted to add are not there.  Please help me to know what I am missing?
Thx,
T.

---

