---
title: "Problem with upgrading to Edgy"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Ed.Corcoran on 2006-10-27
I'm getting an error that's preventing me from updating one of my machines to Edgy. My other two machines upgraded fine, but this one gives me the following error whenever I run "sudo apt-get update". I also get a similar error whenever I do "gksudo update-manager -c". Any ideas why it's happening to this one computer, but not my other two? I'm using a clean sources.list. This computer does have lots of non-6.06 packages installed, though (Firefox 2.0, GnuCash 2.0, museek, Listen, etc.), but that hasn't been a problem before.

```

Get:5 http://archive.ubuntu.com dapper-updates/main Sources [59.6kB]
99% [5 Sources gzip 0]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper-updates/main Sources
  Sub-process gzip returned an error code (1)
Fetched 5B in 3s (2B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by zek725 on 2006-10-29
try replacing dapper to edgy in your sources.lst

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

