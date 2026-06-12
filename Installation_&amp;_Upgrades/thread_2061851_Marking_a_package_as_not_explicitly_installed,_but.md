---
title: "Marking a package as not explicitly installed, but keep it as an installed dependency"
date: 2012-09-23
forum: Installation &amp; Upgrades
---

### Post by Zugzwang on 2012-09-23
Dear all,

due to a bad internet connection, I had to install a piece of software by downloading the two .debs and installing them with dpkg -i.

So I have a package A that depends on B, and I've installed them both by hand.

Now what I want is that if at some point, I remove A, then B gets flagged as a package that is no longer needed, and gets removed, too. **How do I flag package B so that the package manager thinks that B is only installed because it is a dependency.** Note that I don't want to remove A or B at this point, it is just that when I decide to remove A at some point, then B should be removed automatically as well (at least when I do apt-get autoclean).

Thanks!

---

