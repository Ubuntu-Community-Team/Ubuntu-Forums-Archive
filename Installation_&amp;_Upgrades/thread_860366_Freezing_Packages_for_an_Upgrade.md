---
title: "Freezing Packages for an Upgrade"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by bedunbar on 2008-07-15
I am about to upgrade several systems for supporting a project. The first machines to be upgraded will be the development machines. A couple weeks later, we will upgrade our test lab machines, and then in roughly a month, we will upgrade our production servers.

Here is what I need to do. After upgrading development and getting everything working, I need to be sure that the same packages get installed in the test lab and production machines. Even if the upgrade to the production machines happens a month later, and there are updated packages, I need to ensure that it uses the same packages I installed in development as I need the environments to be identical. If it matters, I am going from 6.06LTS to 8.04

Is this doable?

---

### Post by Partyboi2 on 2008-07-16
maybe [[COLOR=Blue]aptoncd[/COLOR]]("http://aptoncd.sourceforge.net/") (also in the repos) could be a option

---

