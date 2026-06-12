---
title: "Some error when make upgrade or some installation"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by myChucky on 2011-01-04
I will get this,

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DEGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEAFailed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/source/Sources.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Somebody help me, please.

---

### Post by smuthavarapu on 2011-01-04
Try change the Server to Main Server in the Update Manager window in Advanced Settings

---

### Post by smuthavarapu on 2011-01-04
Try change the Server to Main Server in the Update Manager window in Advanced Settings

---

### Post by smuthavarapu on 2011-01-04
Try change the Server to Main Server in the Update Manager window in Advanced Settings

---

### Post by smuthavarapu on 2011-01-04
Try change the Server to Main Server in the Update Manager window in Advanced Settings

---

### Post by smuthavarapu on 2011-01-04
Screen shot attached

---

### Post by myChucky on 2011-01-05
> **smuthavarapu said:**
> Try change the Server to Main Server in the Update Manager window in Advanced Settings

I has do like that, but still get this error.

W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE, W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA, W:Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/source/Sources.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/source/Sources.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by smuthavarapu on 2011-01-06
I have found the following information from this post 
[http://ubuntuforums.org/showthread.php?t=279758&page=2](http://ubuntuforums.org/showthread.php?t=279758&page=2)

Basically you need to do the following.

run the command 
wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)

and then open up synaptic
and go to settings>repos>authentication
and "import file key"
browse the key and click ok.

and then do the Update manager.

---

### Post by leeb9972 on 2011-02-09
will not connect, i have same problem, any more ideas?

--2011-02-10 17:48:25--  (try: 3)  [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)
Connecting to packages.freecontrib.org|34.52.53.34|:80... failed: Connection timed out.
Retrying.

--2011-02-10 17:51:37--  (try: 4)  [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)
Connecting to packages.freecontrib.org|34.52.53.34|:80... failed: No route to host.

---

