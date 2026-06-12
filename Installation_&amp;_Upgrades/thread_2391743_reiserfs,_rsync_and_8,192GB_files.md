---
title: "reiserfs, rsync and 8,192GB files"
date: 2018-05-12
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-05-12
I am moving the data on one server to new raid array. I chose to change the files system from reiserfs to ext4. I am transferring the files using rsync.
As I was doing this I found rsync hanging up and reporting it was transferring at hundreds of megabytes per second but nothing was happening, the target filesystem was showing no additional space being used. I looked at the file being transferred and ls reported the files was 8192 GB, which is impossible because the file-system isn't that big. Running reiserfsck showed no errors in the filesystem.

I deleted the obviously corrupt files and will deal with them if necessary. I don't think any of them were really critical.

Has anyone seen this before and if so do you know what caused it?

---

