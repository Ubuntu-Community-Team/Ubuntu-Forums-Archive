---
title: "aptly mirror dist-upgrade"
date: 2017-11-01
forum: Installation &amp; Upgrades
---

### Post by Trevor_White on 2017-11-01
Does anyone here have any good advice on creating aptly mirrors?

I've created a mirror using the following:
```
aptly mirror create -architectures=amd64 -filter='Priority (required) | Priority (important) | Priority (standard) | nginx | mysql | ssh ' trusty-updates http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main
aptly mirror create -architectures=amd64 -filter='Priority (required) | Priority (important) | Priority (standard) | nginx | mysql | ssh ' trusty-security http://security.ubuntu.com/ubuntu trusty-security main

```

I've pointed my remote server which doesn't have internet access to it and successfully done an apt-get update / apt-get dist-upgrade

However during the installation various components are removed such as vim and I'm left with a broken ssh, if I try and start it then it just dies again, if I try and upgrade the same server (it's a VM for testing at the moment) using an internet source it of course updates more modules but the system is in a good state after.

So I was wondering if there was a way to create an aptly mirror to update all Ubuntu 14.04.X system to the latest security patched level whilst keeping the size down?

At this stage I'm thinking the only way is to remove the filter element and cache everything from security.ubuntu.com for trusty as I'm assuming there are some dependency problems in there somewhere, although apt doesn't actually complete but it does say that it's removing some components during the upgrade, I'm assuming because they are no longer in the new apt repository.

Here is the guide I used [https://www.aptly.info/tutorial/mirror/](https://www.aptly.info/tutorial/mirror/)

Thanks in advance

---

