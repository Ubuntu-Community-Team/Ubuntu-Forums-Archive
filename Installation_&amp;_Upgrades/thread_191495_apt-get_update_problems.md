---
title: "apt-get update problems"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by krsnendu on 2006-06-07
I am having problems upgrading from 5.10
I get the following messages from apt-get update
What do I have to do to fix it?

Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [121kB]
91% [6 Packages gzip 0] [Connecting to archive.ubuntu.com (85.133.25.7)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [57.5kB]
92% [Working]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Fetched 382B in 1m48s (4B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by aysiu on 2006-06-07
Try the workaround at the bottom of this page. Otherwise, if that doesn't work, try the top of the page: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by krsnendu on 2006-06-07
I tried clearing sources.list and running sudo apt-get update
That went ok.
When I copied the repository info back in again I get the same error again.

Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [4735B]
93% [31 Packages gzip 0] [Connecting to archive.ubuntu.com (85.133.25.8)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
  Sub-process gzip returned an error code (1)
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [116kB]
93% [32 Packages gzip 0] [Connecting to archive.ubuntu.com (85.133.25.8)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [58.0kB]
93% [33 Sources gzip 0] [Connecting to archive.ubuntu.com (85.133.25.8)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  Sub-process gzip returned an error code (1)
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [48.6kB]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [22.5kB]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.4kB]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [29.3kB]
Fetched 4506kB in 4m37s (16.3kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

