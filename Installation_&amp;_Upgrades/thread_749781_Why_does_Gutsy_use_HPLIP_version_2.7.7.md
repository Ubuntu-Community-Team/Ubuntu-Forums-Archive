---
title: "Why does Gutsy use HPLIP version 2.7.7 ?"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2008-04-08
Why does Ubuntu Gutsy use HPLIP version 2.7.7 (as installed by default) when there appears to be at least 5 HPLIP versions newer than that one on the HPLIP site ?

Thanks.

---

### Post by linuxh8tertoo on 2008-04-08
I found a very good explaination for this here -> [Explanation]("http://openbsd.org")

---

### Post by wpshooter on 2008-04-09
> **linuxh8tertoo said:**
> I found a very good explaination for this here -> [Explanation]("http://openbsd.org")

Can you be a bit more specific as to where this explanation is given ?

I looked at the page but there is nothing that obviously points me to where to go.  I did a search on HPLIP but that did not lead to an explanation.

Thanks.

---

### Post by PmDematagoda on 2008-04-09
> **wpshooter said:**
> Why does Ubuntu Gutsy use HPLIP version 2.7.7 (as installed by default) when there appears to be at least 5 HPLIP versions newer than that one on the HPLIP site ?

Thanks.

This is because the package versions are frozen once an Ubuntu version is officially released, this is so that the stability of the release could be preserved and the dependencies match each other without making any conflicts. 

For your information Ubuntu 8.04 has HPLIP version 2.8.2 and HPLIP(including other packages) will stop upgrading once the archives are frozen on April 10th and they will remain the same unless patches are uploaded(where the version number remains the same) or a new version of a package version is uploaded which does not happen unless the current application necessitates a patch that cannot be used on the current version.

---

### Post by wpshooter on 2008-04-09
> **PmDematagoda said:**
> This is because the package versions are frozen once an Ubuntu version is officially released, this is so that the stability of the release could be preserved and the dependencies match each other without making any conflicts. 

For your information Ubuntu 8.04 has HPLIP version 2.8.2 and HPLIP(including other packages) will stop upgrading once the archives are frozen on April 10th and they will remain the same unless patches are uploaded(where the version number remains the same) or a new version of a package version is uploaded which does not happen unless the current application necessitates a patch that cannot be used on the current version.


Does this mean that I should NOT attempt to use (or it is a bad idea to) a version of HPLIP (or any other packages) higher that which is built-into/installed in Ubuntu versions by default ?

Thanks.

---

### Post by PmDematagoda on 2008-04-09
> **wpshooter said:**
> Does this mean that I should NOT attempt to use (or it is a bad idea to) a version of HPLIP (or any other packages) higher that which is built-into/installed in Ubuntu versions by default ?

Thanks.

It depends on the package itself, if the dependencies between the packages are not much different then a package upgrade would have a good chance of succeeding.

---

