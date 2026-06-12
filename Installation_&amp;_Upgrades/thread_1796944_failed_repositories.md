---
title: "failed repositories"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by Colorado Newb on 2011-07-04
My update manager has recently started giving me the following message:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.170 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Which is odd, since I'm using release 10.04 Lucid.

I usually don't mess with terminal commands but can;t seem to resolve the issue in the update manager.

Any ideas?

---

### Post by karlson on 2011-07-04
Given that us.archive.ubuntu.com is a set of servers it can happen if the server is having an issue.

Easiest way to check:

[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) in any browser.

You can then do the following in the terminal:

```
sudo apt-get update
```

You can also change the name server so that lookup of us.archive.ubuntu.com gives you a different server as primary.

---

### Post by Colorado Newb on 2011-07-04
It looks like I can access the proper repositories (i.e. the ones I've checked in the update manager) but I still get the error message.

It doesn't matter which server I choose, I still get the message.  Is there a safe way for me to use the command line to tell the update manager to stop looking for the failed Jaunty repositories?

---

### Post by oldos2er on 2011-07-04
Support for Jaunty ended last October. You should edit your sources.list and remove references to anything except Lucid.

---

### Post by Colorado Newb on 2011-07-04
Thanks Ann, that's exactly what I'd like to do.  Can you give me an example of a command that I would use to do that?

---

### Post by oldos2er on 2011-07-04
```
gksu gedit /etc/apt/sources.list
```

---

### Post by Colorado Newb on 2011-07-06
Thank you Ann.  That did the trick.

---

### Post by oldos2er on 2011-07-06
You're welcome.

---

