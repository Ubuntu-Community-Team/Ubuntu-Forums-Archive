---
title: "nfs-common borked"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hikaricore on 2009-10-03
```
Preparing to replace nfs-common 1:1.2.0-2ubuntu1 (using nfs-common_1%3a1.2.0-2ubuntu1_i386.deb) ...
Unpacking replacement nfs-common ...
Setting up nfs-common (1:1.2.0-2ubuntu1) ...
 * Stopping NFS common utilities                                                                                    [ OK ]
 Removing any system startup links for /etc/init.d/nfs-common ...
statd start/running, process 22131
start: Job failed to start
invoke-rc.d: initscript gssd, action "restart" failed.
dpkg: error processing nfs-common (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nfs-common

```

Ended up having to try and install this package manually with dpkg since nfs-kernel-server refused to install previously.
The issue though out the install has been the same post-installation script failure.
Tried with several force/ignore flags to no avail.

Anyone else encountered this?

---

### Post by Elfy on 2009-10-03
yep - same here 

patiently waits ... 

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/441055](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/441055)

---

### Post by hikaricore on 2009-10-03
It's fixed :p

---

### Post by Elfy on 2009-10-06
a few updates have gone through here but I still get the same issue on boot.

The update manager gives me

> Setting up nfs-common (1:1.2.0-2ubuntu4) ...
Installing new version of config file /etc/init/rpc_pipefs.conf ...
Installing new version of config file /etc/init/gssd.conf ...
Installing new version of config file /etc/init/idmapd.conf ...
statd start/running, process 21809
start: Job failed to start
invoke-rc.d: initscript gssd, action "restart" failed.
start: Job failed to start
invoke-rc.d: initscript idmapd, action "restart" failed.

---

### Post by richardh9936 on 2009-10-13
My eee-pc 1000 (NBR) is affected, too.  Its symptoms include a missing file -  "/etc/init.d/nfs-common".  However, in Launchpad, [bug #441855]("https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/441855") Steve says he's fixed this.

If so, how do I retrieve the fixed modules?  Synaptic doesn't update nfs-common, nor nfs-kernel-server, and it doesn't list nfs-utils.

---

### Post by stucky on 2009-10-18
Still happening

---

### Post by xlnt01 on 2009-10-20
happens here to...

This is what I get when I update

Setting up nfs-common (1:1.2.0-2ubuntu8) ...
statd start/running, process 16220
gssd stop/pre-start, process 16243

And then it just sits there and nothing happens.

---

