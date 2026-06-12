---
title: "Error in Maverick Repository?"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Geryon on 2010-10-12
I am trying to install tzdata-java and I think I've stumbled across an error in the Maverick repository on us.archive.ubuntu.com. 

I originally thought there was a package error and created this post over in 'general help': [http://ubuntuforums.org/showthread.php?t=1594394](http://ubuntuforums.org/showthread.php?t=1594394)

However, I really think this is a repository problem.  If I clear my cache out and run 'apt-get update' again I see that it's still referring to this file for tzdata:

[http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010m-0ubuntu0.10.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010m-0ubuntu0.10.04_all.deb)

Yet, looking through the repository a maverick version exists:

[http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010m-0ubuntu0.10.10_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010m-0ubuntu0.10.10_all.deb)

Secondly, I am trying to install 'tzdata-java' and the repository insists on trying to install this file and failing:

[http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2010l-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2010l-1_all.deb)

Which is an even older version.  So I am not quite clear what is going on here.  Here's snippets from what is my local repository pulled down from 'us.archive.ubuntu.com' after clearing my cache:

$ apt-cache search --full tzdata

Package: tzdata-java
Priority: optional
Section: libs
Installed-Size: 1916
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: all
Source: tzdata
Version: 2010l-1
Depends: tzdata (= 2010l-1)
Filename: pool/main/t/tzdata/tzdata-java_2010l-1_all.deb


Package: tzdata
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 6276
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 2010m-0ubuntu0.10.04

So it looks like things are out of sync.

---

### Post by Geryon on 2010-10-13
I just noticed that this has been resolved.  tzdata now has the proper version and the tzdata-java package as well.  Both are installed on 10.10 just fine.

---

