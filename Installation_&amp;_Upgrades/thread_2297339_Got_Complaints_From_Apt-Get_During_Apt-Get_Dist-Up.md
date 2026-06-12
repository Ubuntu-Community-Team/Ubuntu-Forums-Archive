---
title: "Got Complaints From Apt-Get During Apt-Get Dist-Upgrade"
date: 2015-10-02
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2015-10-02
I got the following complaints from apt-get during today's manual update process```
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'

```
I've no idea what to do about it.  Can someone help please?

---

### Post by tgalati4 on 2015-10-02
[MIME]("https://help.ubuntu.com/community/AddingMimeTypes") types are file types that invoke a specific action when clicked on.  Some file types have no actions associated with them.  That is normal.

If you are having trouble, generally:

```
sudo apt-get clean
sudo apt-get check
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by vasa1 on 2015-10-03
[http://askubuntu.com/questions/456183/what-does-unknown-media-type-in-type-all-all-mean](http://askubuntu.com/questions/456183/what-does-unknown-media-type-in-type-all-all-mean)
[http://ubuntuforums.org/showthread.php?t=2208433](http://ubuntuforums.org/showthread.php?t=2208433)
[https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/289592](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/289592) from 2008

---

