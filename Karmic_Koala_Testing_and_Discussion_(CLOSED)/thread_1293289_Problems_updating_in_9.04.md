---
title: "Problems updating in 9.04"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hapkidoman on 2009-10-16
Hi everyone.  For the past week, I have had a red triangle-alert icon in my menu that tells me that Karmic Koala is not fully updated and that it could be due to repository errors or a network problem.  

I don't seem to be having any problems updating; however.  I manually update (because it doesn't automatically search for updates).  However, I am told that I can not get all updates because of these errors:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/karmic/Release](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/karmic/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://apt.boxee.tv/dists/karmic/main/binary-i386/Packages.gz](http://apt.boxee.tv/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Does anybody have any idea as to how I can get the public key for Karmic Koala as well as fix the other problems?

Thanks in advance guys.....so far, I haven't had any major problems with the beta version, hopefully I can get this fixed so I can have all the updates, however.

---

### Post by oboedad55 on 2009-10-16
> **hapkidoman said:**
> Hi everyone.  For the past week, I have had a red triangle-alert icon in my menu that tells me that Karmic Koala is not fully updated and that it could be due to repository errors or a network problem.  

I don't seem to be having any problems updating; however.  I manually update (because it doesn't automatically search for updates).  However, I am told that I can not get all updates because of these errors:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/karmic/Release](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/karmic/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://apt.boxee.tv/dists/karmic/main/binary-i386/Packages.gz](http://apt.boxee.tv/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Does anybody have any idea as to how I can get the public key for Karmic Koala as well as fix the other problems?

Thanks in advance guys.....so far, I haven't had any major problems with the beta version, hopefully I can get this fixed so I can have all the updates, however.

Those are repo errors. Those repos you have quoted either need to be removed or the public keys gotten. Otherwise the errors won't hurt anything, they're just annoying. If you have karmic installed, unless you changed something, then you're all set.

---

### Post by hapkidoman on 2009-10-16
How do I remove them or get the keys for them?  I'm not new to Ubuntu, but I'm new to this particular aspect of it.  Also...thanks for you help :)

---

### Post by oboedad55 on 2009-10-16
> **hapkidoman said:**
> How do I remove them or get the keys for them?  I'm not new to Ubuntu, but I'm new to this particular aspect of it.  Also...thanks for you help :)

Sure, just go to the software repos in synaptic and look for the "other software" section and highlight them and hit "remove".

---

