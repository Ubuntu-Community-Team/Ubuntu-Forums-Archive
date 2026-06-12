---
title: "packages for 10.04.2 vs 10.04.1 etc"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-05-25
Are the package sets the same for 10.04.2 as for 10.04.1 and 10.04?  If I were to extract a full set of packages using apt-cache dump, would I get the same list on these versions?

---

### Post by snowpine on 2011-05-25
They are snapshots of the same thing. If you apply regular updates then you are have the latest whether you installed 10.04, 10.04.1, etc.

---

### Post by Skaperen on 2011-05-25
> **snowpine said:**
> They are snapshots of the same thing. If you apply regular updates then you are have the latest whether you installed 10.04, 10.04.1, etc.
What if the only thing ever done was just "apt-get update" (e.g. no actual packages were upgraded)?  I'd expect different packages.  But this should be the same *list* of packages, right?  If I were to do "apt-get --yes dist-upgrade" on each of these, then I'd be at an identical set of packages on all these machines?

---

### Post by tgm4883 on 2011-05-25
> **Skaperen said:**
> What if the only thing ever done was just "apt-get update" (e.g. no actual packages were upgraded)?  I'd expect different packages.  But this should be the same *list* of packages, right?  If I were to do "apt-get --yes dist-upgrade" on each of these, then I'd be at an identical set of packages on all these machines?

You would most likely get the same list of packages (there are only a few very specialized cases I can think of where they would differ). The difference would be that the 10.04.2 would have newer package versions than 10.04.1. Basically 10.04.2 is just a snapshot in time, as is 10.04.1, as is 10.04

---

### Post by snowpine on 2011-05-25
> **Skaperen said:**
> What if the only thing ever done was just "apt-get update" (e.g. no actual packages were upgraded)?  I'd expect different packages.  But this should be the same *list* of packages, right?  If I were to do "apt-get --yes dist-upgrade" on each of these, then I'd be at an identical set of packages on all these machines?

You are correct that if you use "apt-get dist-upgrade" instead of "apt-get upgrade" you will arrive at the same package list.

"man apt-get" will give you more details.

---

### Post by Skaperen on 2011-05-25
Thanks all.  I just wanted to be sure 10.04.2 and 10.04.1 were not simply (later) branches of 10.04 in terms of the repository.  So if a package is added, it's there for 10.04 and 10.04.1 and 10.04.2.  If I want to generate a list of all available packages for all currently supported versions, doing so separately for 10.04 and 10.04.1 and 10.04.2 is redundant.

---

