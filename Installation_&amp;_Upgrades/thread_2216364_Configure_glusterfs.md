---
title: "Configure glusterfs"
date: 2014-04-11
forum: Installation &amp; Upgrades
---

### Post by gopukrishnan on 2014-04-11
Hi,

Hope you are fine.

I am trying to configure gluster in my rackspace cloud ubuntu servers. I have installed fuse and glusterfs packagaes but glusterfs is not running at all. Could you please guide me through installation in ubuntu serves ? Below are the steps I have tried.

apt-get install libfuse2
apt-get install  fuse-utils
apt-get install glusterfs-server
service glusterd start

root@test1:~# service glusterfs-server status
 * GlusterFS server is not running.

root@test1:~# gluster peer probe test2
-bash: gluster: command not found

So I am stuck here from the remaining steps. Please let me know if I missed something. In btw I shall try to find the solution from some other sources too.

Thanks,

---

