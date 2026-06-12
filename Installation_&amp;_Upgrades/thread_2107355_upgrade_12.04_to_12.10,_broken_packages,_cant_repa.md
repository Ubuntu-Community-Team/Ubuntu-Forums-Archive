---
title: "upgrade 12.04 to 12.10, broken packages, cant repair"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by gloww on 2013-01-21
Hallo,

i am sure this topic was posted here thousand times. i am posting it again because i think i have a slightly different issue. I tried upgrading from 12.04 to 12.10 when 12.10 was still beta. this first try failed because of broken dependencies. now as 12.10 is stable i tried it again and it failed again. i am getting the following error:

```
An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.
```After that i tried to repair the broken packages in different ways. in synaptic no broken packages were shown. i also tried:

apt-get clean / autoclean / -f install and so on.

i am stuck.
maybe someone here has an idea what i can do to solve the problem.

---

