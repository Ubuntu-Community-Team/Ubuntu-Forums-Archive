---
title: "edgy drdb install"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by drjava on 2007-01-11
Hi,

I was wondering if anyone has gotten drdb 0.7 installed on Edgy (2.6.17-10-generic) yet?

I tried the same steps I used with dapper:

sudo apt-get install linux-headers-`uname -r`
sudo apt-get install drbd0.7-modules-source
sudo m-a a-i drbd0.7-module-source

The module assistant dies complaining with:

make[2]: Entering directory `/usr/src/modules/drbd/drbd'

    Calling toplevel makefile of kernel source tree, which I believe is in
    KDIR=/lib/modules/2.6.17-10-generic/build

mv: missing destination file operand after `drbd_buildtag.c{.new,}'
Try `mv --help' for more information.
make[2]: *** [drbd_buildtag.c] Error 1


I must have missed something and I'm at a loss.

Any ideas?

---

### Post by ketso on 2007-01-16
Hi,

You'll find info here: [https://launchpad.net/ubuntu/+source/drbd0.7/+bug/68481](https://launchpad.net/ubuntu/+source/drbd0.7/+bug/68481)

Regards,
Ketso

---

### Post by drjava on 2007-01-16
Many thanks.  I'll give those suggestions a whirl.  (and the bug page is now bookmarked)

---

