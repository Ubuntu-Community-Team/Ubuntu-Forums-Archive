---
title: "Generic Kernel Compilation and modules - Ubuntu 8.04 TLS to support 64 GB"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by jreinis on 2008-06-08
The Task - to change somewhere somewhat to get generic kernel supporting till 64GB (desktop). Server version do not offer.

I understand I need to edit existing .config and (modules or do not? )
with ALL existing settings nothing changing except to support memory till 64GB 
(now my system sees 3.5GB only) because new motherboard goes with 4/8GB memory chips and more import for me 
I use virtualbox and vmware OS images(to develop and to use some applications for windows and apple platforms)

So, I did these steps-by-steps guide

1. sudo apt-get install linux-kernel-devel fakeroot build-essential
2. sudo apt-get build-dep linux-image-$(uname -r)
3. apt-get source linux-image-$(uname -r)
4. sudo apt-get build-dep linux-ubuntu-modules-$(uname -r)
5. apt-get source linux-ubuntu-modules-$(uname -r)

Now I confuse:
What command I run to edit file ".config" ?
Is that place /usr/src/linux-headers-2.6.24-18-generic right?

CONFIG_HIGHMEM64GB is it enough?

Next command I did not get at all :
AUTOBUILD=1 fakeroot debian/rules binary-debs
What does it mean practically and I did not find directory "debian"?

Any help from guys who really compiled EXISTING Ubuntu 8.04 ONLY kernel settings (not new one and not 7.04 old one because in Hardy Heron were changed commands and HOWTO recompile)?

My system is Ubuntu Hardy Heron 8.04 with generic kernel.

---

