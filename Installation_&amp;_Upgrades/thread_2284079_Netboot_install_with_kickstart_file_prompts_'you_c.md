---
title: "Netboot install with kickstart file prompts 'you chose not to install GRUB'"
date: 2015-06-26
forum: Installation &amp; Upgrades
---

### Post by psr888 on 2015-06-26
However I do have bootloader specified in kickstart:

bootloader --location=mbr

My partition config is as follows (I tried using autopart but it doesn't seem to work and I get a prompt for partitions during installation):

part swap --size 1024
part / --fstype ext4 --size 4096 --grow --asprimary

I am trying to create a completely automated install for datacenter servers, hence can't have any prompts in install.

I do have two disks on the machine and I didn't specify location as I came across some posts that say --location parameter causes problems. Could this be related to two disks?

Any help would be greatly appreciated! Thanks!

---

### Post by jason116 on 2016-03-31
Were you able to figure this out? I'm having the same problem.

---

### Post by oldos2er on 2016-04-01
Please start a new thread. psr88 hasn't returned to the forums since last June.

Closed.

---

