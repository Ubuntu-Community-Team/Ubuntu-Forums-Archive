---
title: "sharing the same /usr partition"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by shadowflower on 2008-11-28
it it possible for 2 different linux distro (ex. Ubuntu and OpenSuse) to share the same /usr partition?

---

### Post by lswb on 2008-11-28
There will certainly be conflicts with locations of files in some of the /usr subdirectories, not to mention problems with incompatible binaries, name conflicts, etc. I wouldn't even want to try sharing it between 2 ubuntu versions like hardy and intrepid. You could possibly use the same partition to store 2 separate directories, though, and symlink or use some fancy mount options to link to the correct one for each distribution.

---

