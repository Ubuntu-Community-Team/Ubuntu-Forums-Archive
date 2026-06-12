---
title: "Update not working with Australian server"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-10-06
For some reason I get an error when trying to update with the Australian server. I need to do this as my internet would make it take many hours to update from the main server.

W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 57B0CE6D09827771, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.bz2)  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by alexmurray on 2009-10-06
Try selecting the optus server instead which is also in Australia and for me has better bandwidth anyway.

---

### Post by andrew.46 on 2009-10-07
Hi Sashin,

I experienced a few oddities with Australian servers recently. Somebody reminded me of the nice utility that pings all servers to find the best connection and this resolved my connection and speed issues. I attach a screenshot...

Andrew

---

### Post by Sand &amp; Mercury on 2009-10-07
I was having a lot of troubles with servers till I tried the method andrew.46 mentioned above me a few days ago. Since then things have been fine; using Optus' server.

---

### Post by Sashin on 2009-10-07
Hmm... it seems to work, I got some pacific server.

---

### Post by taavikko on 2009-10-07
just a side note, different servers might be out of sync, so don't wonder if an update is delayed...

[https://edge.launchpad.net/ubuntu/+archivemirrors](https://edge.launchpad.net/ubuntu/+archivemirrors)

---

