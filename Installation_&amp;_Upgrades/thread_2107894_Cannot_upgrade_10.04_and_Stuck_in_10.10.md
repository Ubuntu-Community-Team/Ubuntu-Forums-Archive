---
title: "Cannot upgrade 10.04 and Stuck in 10.10"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by benpptung on 2013-01-23
I made a mistake.

I tried to upgrade my Ubuntu from 10.04 LTS.
Then, I upgraded to 10.10.

It's really funny, then, the system tells me this is an unsupported version, and I cannot upgrade to another unsupported version target. :confused:

So, I think this is an issue for Ubuntu community.
10.04 is a LTS version, which should provide a way for the user to upgrade to 12.04 directly. Or at least, no wrong message for the user to upgrade to 10.10, and leave them there without a way to upgrade.

While I click 'upgrade' in 10.10,  I got the following error message.

W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Appreciated if anyone can help, how can I proceed to upgrade Ubuntu. :o

---

### Post by Warren Hill on 2013-01-23
Ubuntu 10.04 should have allowed you to upgrade directly to 12.04.  But you upgraded to a now unsupported version.

Personally I would first make sure I had a good set of backups then do a clean install of 12.04 but it is possible to upgrade instead.  I have no personal experience but I know people who have done it this way.  Take a look here
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by JRV on 2013-01-23
I have to agree with Warren Hill.  
A backup and fresh install would be better.
I would choose 12.04 LTS, because LTS versions are my preference.

The addition of Unity and the change from GTK2 to GTK3 12.04 are hugh.
There is a lot of chances for problems with that many changes.

---

