---
title: "Problem while upgrading to 8.04"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by vnweb on 2008-05-16
Hi!

I got a problem with the update manager. I'm currently using Ubuntu 7.10.

When i try to "check" (refresh) my list with updates, i got this message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Someone knows what this could be, or how to fix it?

Help will be appreciated:)

---

### Post by bobnutfield on 2008-05-16
Yes, it just means that the key to authenticate the downloads from medibuntu is not in your repository.  Just go to medibuntu's site and download the key.  The instructions for doing so are on the site.

Regards

Bob

---

### Post by bobnutfield on 2008-05-16
If you have any difficulty, just type this in a terminal and it will install the key for you.  

[sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list]("sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list")

---

### Post by bobnutfield on 2008-05-16
Sorry, re-reading you post, I notice that it is complaining about the dapper release GPG key, and you are running Gutsy, but want to upgrade to Hardy.  Disable any third party repositories and try the update again.  If you are going to upgrade Gutsy to Hardy, I believe it will automatically disable third party repos until the upgrade is complete.

If someone else knows a different course, please advise

Bob

---

