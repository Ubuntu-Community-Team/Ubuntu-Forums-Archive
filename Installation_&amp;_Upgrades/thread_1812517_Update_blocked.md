---
title: "Update blocked"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by adil_mhaisker on 2011-07-26
Hi,
I am new to Ubuntu, although old in Linux.

Last month I installed Ubuntu 11.04 and I am not able to update anything using ***apt-get update***. I am getting error which I have mentioned below.
Please notice that I can install applications from ***apt-get install blah***.
The error I am getting after issuing command ***apt-get update*** is as follows..

**[COLOR="Red"]W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages  Hash Sum mismatch[/COLOR]**
.
I have tried everything in Google and Ubuntu forums as well.... No Luck yet.
Please help...

---

### Post by mikewhatever on 2011-07-26
Try clearing the cached packaged with **sudo apt-get clean**. Hopefully that will also get rid of the package with the hash mismatch.

---

### Post by adil_mhaisker on 2011-07-27
Tried that too, NOT working...
Same error message. :(

---

### Post by dino99 on 2011-07-27
glance at synaptic repo tabs, and be sure they are activated (main, universe, multiverse, ...)

or look at logs to find some usefull errors

---

### Post by Sef on 2011-07-27
Have you tried a different mirror? Perhaps the one that you are on has a bad package.

---

