---
title: "Create Resize Move LVM Partition"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by opticyclic on 2010-09-02
As mentioned  [here]("http://ubuntuforums.org/showthread.php?t=1565959") I am planning on installing with encryption.
This involves using LVM in the partition scheme.
I am following this guide here which uses Mandriva to do the installation.
[http://www.linuxbsdos.com/2010/07/18/how-to-configure-encrypted-lvm-on-mandriva-2010-spring/](http://www.linuxbsdos.com/2010/07/18/how-to-configure-encrypted-lvm-on-mandriva-2010-spring/)

However, I notice that GParted doesn't seem to have any support for LVM, which is going to be a pain in the rear if I subsequently try to add Ubuntu to the Mandriva boot setup.

The problem I have with DiskDrake (Mandrivas partition editor) is that it only seems to be able to put partitions at the beginning of the drive and it doesn't seem to be able to move partitions.
e.g. if I want to create a new partition at the end for swap and leave some unallocated space in the middle for my future Ubuntu installation I am stuck.
GParted allows me to create at the end or effectively move it by resizing the beginning and end of the partition.
DiskDrake allows me to create and edit LVM partitions.

Is there perhaps another partition editor that does both?
Or maybe a development version of one that does it? 
Or some option I am missing?

---

### Post by opticyclic on 2010-09-02
OpenSuse have an application as part of Yast2 called 'Expert Partitioner' that seems to handle LVM quite well.
Fedora/RedHat have one called Disk Druid as part of their installer Anaconda.

Unfortunately these are both rpm based distros and don't seem to be available for debian based distros.
Even worse, Disk Druid doesn't seem to be extractable from Anaconda as a separate package.

What I did find that is sort of OK is [system-config-lvm]("http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/Deployment_Guide-en-US/s1-system-config-lvm.html")
Even though this is from RedHat as well, there is a version in the repositories that can be used.

Is there anything better around?

---

### Post by srs5694 on 2010-09-03
You could look into kvpm. I've not used it or system-config-lvm to be able to say which is better, but they're both GUI LVM manipulation tools.

---

