---
title: "e2fsck: Get a newer version of e2fsck!"
date: 2019-04-04
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2019-04-04
I am trying to check/fix certain HDD filesystem however encountered this issue. 

```
$ sudo fsck -M /dev/sda5
[sudo] password for user:
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sda5 has unsupported feature(s): metadata_csum
e2fsck: Get a newer version of e2fsck!

```
What should I do? The HDD contains Ubuntu 18.04. I ran the above fsck command from a different storage disk that uses Ubuntu 16.04.

---

### Post by Rubi1200 on 2019-04-04
I think this post might contain the answer for you:
[https://askubuntu.com/questions/1053404/e2fsck-how-to-handle-the-metadata-csum-error-by-advancing-the-e2fsck-version?noredirect=1&lq=1](https://askubuntu.com/questions/1053404/e2fsck-how-to-handle-the-metadata-csum-error-by-advancing-the-e2fsck-version?noredirect=1&lq=1)

Seems it boils down to a version compatibility problem.

---

