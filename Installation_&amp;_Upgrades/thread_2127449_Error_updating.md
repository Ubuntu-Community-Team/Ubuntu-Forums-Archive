---
title: "Error updating"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by charlescarroll1 on 2013-03-20
*I found the solution to my problem right before I posted my question. I decided to post anyways just in case someone else is having the same issue*

When using Software Updater I got the following error message:

> Failed to download repository information
Check your Internet connection.

Details
W:GPG error: [http://apt.insynchq.com](http://apt.insynchq.com) quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 06BBDC2602DFE7E7, W:Failed to fetch [http://apt.insynchq.com/ubuntu/dists/quantal/non-free/source/Sources](http://apt.insynchq.com/ubuntu/dists/quantal/non-free/source/Sources)  403  Forbidden
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I received the same message when running sudo-apt get update.

It turns out that the issue lies with the "insync" source - an application I used to use when I tried integrating Google Drive. It didn't work as well as I'd hoped so I removed it quite a long time ago but the entry remained as a software source. It turns out that it was still being used as a source when I tried updating thus indicating that the problem lies with their servers.

I removed the insync entries by opening up software sources and deleting the [http://apt.insynchq.com/ubuntu](http://apt.insynchq.com/ubuntu). I can now update with no error.

I think it's odd that this one source was preventing me from updating my system.

---

### Post by antvyanka on 2013-04-26
Thank you, I was just having this problem.

---

