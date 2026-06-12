---
title: "New PHP installation slow"
date: 2014-11-05
forum: Installation &amp; Upgrades
---

### Post by Glenn_Thomas_Hvids on 2014-11-05
I had an old 10.04 installation with Apache and PHP. This retrieved data from another server running MySQL. This has worked fast and flawlessly these last few years.
Now I installed a brand new 14.04, also with Apache and PHP, and transferred all my sites from the old server to the new one. My sites are equally fast and flawless except for one issue. Getting binary data (BLOB) from the database has suddenly turned really slow when executing multiple queries.
On the old server getting all the BLOBs (some times with as many as 40 queries) for one page was performed quite quckly.
However, on the new server, getting the same BLOBs can now suddenly take up to a minute. Getting a single BLOB seems to go as quickly as on the old one. The issue only appears when there are several.
Because this only happens on the new server and not the old one I figure it must have something to do with either the Apache or PHP configuration, also that is has something to do with "connections", but I just can't figure out what or where.
Both old and new server are VMs, by the way, but with identical setup for CPU, Memory, disk usage (et al), so the specs on the server itself shouldn't be an issue.

Does anybody have any pointers as to why the data extraction is slow on the new server and quick on the old one?

---

