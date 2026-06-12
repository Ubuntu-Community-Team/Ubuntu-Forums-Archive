---
title: "My first Ubuntu installation - Partition utility frustrations."
date: 2013-05-28
forum: Installation &amp; Upgrades
---

### Post by 5y5t3m5hark on 2013-05-28
Hello all!

Old school Linux user here who decided to try Ubuntu for the very 1st time.  Loving it!!!  I've been using Fedora on my primary machine for about the last 6 years, but I digress.  Anyway, I installed Ubuntu 13.04 last night after backing up my Fedora 18 /home DIR so that I may blow away all partitions and start fresh with Raring.  When the installer offered me my chance to customize partitioning, I discovered that the `-` button (i.e. delete) was always disabled for all LVM VGs.  I was however able to delete the /boot non-LVM partition.  Why are existing LVM slices un-delete-able?  Am I just missing something?  To get through the install with fresh LVM partitioning, I chose to boot my Fedora 18 DVD, customize my disks LVM, apply partitioning/formatting via a minimal Fedora install and then boot the Ubuntu installer and simply edit the LVM attributes I created using the Fedora installer's partition utility.  In the end, my system is partitioned properly, but can someone tell me what I missed as I cannot fathom that this prevention is by design.

Thoughts appreciated and thank you in advance.

**--**
**lpshark**
ubuntu 13.04 / centos 6.3 / fedora 18 / rhel 6.3
*asus g73jw-a1 (intel® core™ i7-740qm - 2.93ghz, 8 gb ram, nvidia geforce gtx 460m - 1.5 gb vram, 2 x 500 gb seagate xt ncq solid state hybrid drives)*

---

### Post by ahallubuntu on 2013-05-28
~

---

