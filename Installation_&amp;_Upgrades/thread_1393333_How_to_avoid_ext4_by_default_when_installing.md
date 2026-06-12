---
title: "How to avoid ext4 by default when installing?"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by narcisgarcia on 2010-01-29
This is the related question in Launchpad:
[https://answers.launchpad.net/ubuntu/+source/partman-ext3/+question/98607](https://answers.launchpad.net/ubuntu/+source/partman-ext3/+question/98607)
and it may affect to debian-installer configuration (?)

How can I do to avoid that in the **alternate** installation partitioner doesn't appear "ext4" filesystem **as the default** selection in any step?

This could make able to install to an encrypted independent volume, for example, without crashing partman-ext3:
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/503848](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/503848)

---

### Post by louieb on 2010-01-29
manual partitioning - use as - choose whatever file-system you want from a list.

---

### Post by narcisgarcia on 2010-01-29
As you could see in the bug report, when you do this in a manual partitioning method and encrypted volume, partitioner crashes in the moment you enter to the "ext4" value to be changed.

I need to find that value already set to "ext3" to avoid the crash.

---

