---
title: "Some problems encountered during Xubuntu installation (edgy)"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by Hatta on 2006-11-26
The first problem was that I already had partitions (from an old dapper installation), so I wanted to use them, but the installer didn't want to recognize that I had chosen a root partition (also marked for reformatting). I solved that problem by deleting the partition and creating a new one in its place (reiserfs like the newly deleted was). That worked for a short while into the installation before it crashed (exit code 139). After I tried it once more I decided to test with ext3 instead which worked better until the installation was almost finished, at which time it crashed (exit code 1). As I type this I'm doing a second attempt.

Also Firefox refused to work (shutdown immediately after it had started) from sometime into the first installation (the first attempt with reiserfs) until I started the third (first ext3 attempt).

*update* Installation number 4 (second with ext3) also failed. This time I checked at what stage, and it was removing packages.

---

