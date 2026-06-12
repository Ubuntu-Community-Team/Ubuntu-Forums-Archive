---
title: "Prob: Cyclic dependencis and  immediate configuration"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by it.henrik on 2008-02-02
Hi all,

My ubuntu installation borked on me a while ago after I did an upgrade of some sw (dont remember which).

My ubuntu installation did not boot so I had to boot from CD and then chroot onto the borked filesystem and reinstall  ALOT of broken packages.

Now I can boot and get into X but some things are still not working.

I was planning on reinstalling all installed packages with synaptics to solve whats still broken.

What I done in synaptic:

Filtered out all installed packages.
Marked them as "Reinstall package"
Apply.

First thing I run into is:
E: Couldn't configure pre-depend coreutils for dpkg, probably a dependency cycle.

so if I remove coreutils from the list with packages to reinstall I get a little further but then I get:
E: Internal Error, Could not perform immediate configuration (2) on gzip

I just keep on getting the same message for other packages, ie python etc

What can I do to help synaptic solve these problems? :confused:
I have reinstalled  gzip, dpkg  and coreutils seperately and that went fine.

---

