---
title: "Can Upgrade Preserve Config and Write New?"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2008-03-10
This question is looking ahead to upgrading to Hardy Heron, 8.04. 

Is there a way to upgrade to the next release, have the current configuration (/etc/hosts, /etc/services, networking, and so on) preserved, but have the upgrade write its default configuration without being prompted?

I have found that Ubuntu upgrades go much better when I let the installation overwrite what's there. I am wondering if the upgrade preserves certain files with a unique file extension, or if I just need to backup what's unique in my system? 

Most of this "uniqeuess" is under /etc.

Thanks.

---

### Post by Rocket2DMn on 2008-03-10
When I upgraded to Gutsy, I was asked a few times if I wanted to overwrite some files, but I don't recall which ones.  To be very sure, you can make backups of any files you want to keep or refer to later, they shouldn't be touched during the upgrade, esp. if you store them somewhere else.
Something along these lines:
```
sudo cp /etc/hosts /etc/hosts.gutsy.bak
```

---

