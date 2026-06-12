---
title: "remove packages for which I have not used an owned file"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by keratos2 on 2014-08-08
Thinking of writing a little script that recurses the filesystem and for each file identifies last access time and marks the package owning the file  together with the access time; if an access time is newer then the current marked package then the access time becomes the newer (most recent); then,for each marked package, list the package name and last access time. This will provide a list of packages and the date on which it was it was last accessed; from this I can determine whether I have ever used a package (i.e. any file in it) or when I last accessed a package (i.e a file in it)

This will allow me to remove packages I dont use or use infrequently

Yes Yes Yes - I know all the usual caveats and warnings and views - please dont post - but if anyone has heard of an app that does this under linux , do let me know.

p.s. I could do the reverse and scan all filenames in  a package then access the file in the system to determine the atime
Cheers

---

