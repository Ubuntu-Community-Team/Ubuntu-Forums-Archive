---
title: "fresh install over existing software raid 1, keep home partition &lt;-- does not work."
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by whoop on 2010-04-24
I tried a fresh install over an existing install keeping the /home partition intact. This works fine.

However, doing the same thing over a software raid 1 installation (raid 1 array for /, raid 1 array for /home, raid raid 1 array for swap) does **not** work, I also tried different configurations (only a raid 1 /home for instance).
When I try this I get:
Failed to remove conflicting files
The installer needs to remove operating system files from the install target, but was unable to do so, The install cannot continue.

I posted a bug report on this a while ago, but it's not active at all:
[https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/560152](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/560152)

Can't seem to think this is not important. Hope I am doing something wrong.
Is anyone experiencing this, does anyone care to reproduce and confirm this?

cheers

---

### Post by whoop on 2010-04-27
Looks like it's fixed in the daily builds...

---

