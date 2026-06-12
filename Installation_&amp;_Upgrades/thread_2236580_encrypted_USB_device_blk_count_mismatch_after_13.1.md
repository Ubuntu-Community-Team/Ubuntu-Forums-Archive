---
title: "encrypted USB device blk count mismatch after 13.10-&gt;14.04 upgrade"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by frankdn01 on 2014-07-27
Hello and thanks in advance!

As the subject says, I cannot mount an encrypted USB device following the upgrade to 14.04.  When inserted, the password dialog is presented but then the mount fails.

dmesg | tail produces this:

[ 1148.232465] EXT4-fs (dm-0): bad geometry: block count 524288 exceeds size of device (507771 blocks)

I haven't touched a thing (so far).

---

