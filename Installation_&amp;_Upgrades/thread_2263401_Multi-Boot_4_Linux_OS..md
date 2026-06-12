---
title: "Multi-Boot 4 Linux OS."
date: 2015-01-31
forum: Installation &amp; Upgrades
---

### Post by oceola2 on 2015-01-31
Noticed a number of posts where another dual booted OS is not being "seen." Am relating the following as it may help somewhere down the line for someone:
Have been running Linux14.04 LTS and 12.04.5 for some time with an older version of Linux Mint and another drive blank.
Decided to remove the Linux Mint old version and replace it with Fedora 21 but due to a repository error and some partition noises wound up putting LinuxMint17 in it's place and placing Fedora 21 on the blank RE4 drive.
One of the things I noticed when running update-grub was neither Ubuntu14.04 or 12.04.5 seemed to "see" the Fedora 21 install.
I tried update-grub with the Linux Mint install and it saw all four operating systems.
When updating the kernel today I found  a file **CLVM** and it's dependencies which, when running 14.04LTS actually showed Fedora 21 after install when running update-grub.

Cluster LVM Daemon for lvm2 
This package provides the clustering interface for lvm2, when used with Red Hat's "cman" or corosync based (eg Pacemaker) cluster infrastructure.
It allows logical volumes to be created on shared storage devices (eg Fibre Channel, or iSCSI).

This is the file and the list of dependencies.
Commit Log for Sat Jan 31 14:32:53 2015
Installed the following packages:
clvm (2.02.98-6ubuntu2)
libcmap4 (2.3.3-1ubuntu1)
libcorosync-common4 (2.3.3-1ubuntu1)
libcpg4 (2.3.3-1ubuntu1)
libdevmapper-event1.02.1 (2:1.02.77-6ubuntu2)
libdlm3 (4.0.1-0ubuntu1)
libqb0 (0.16.0.real-1ubuntu3)
libquorum5 (2.3.3-1ubuntu1)
lvm2 (2.02.98-6ubuntu2)
watershed (7)

---

### Post by oldfred on 2015-02-01
Many who multi-boot do not install Fedora (or any of its family) using the default LVM, but just use standard partitions.
But if you do install Fedora with LVM you normally have to install the lvm2 package and mount the Fedora partition so os-prober can 'see' the Fedora files. 
Or you add lvm2 driver and just copy the boot stanza from Fedora into the grub2 40_custom that is in MBR. 
If several drives you can have different copies of grub in each drive to boot the install on that drive if desired.
       sudo apt-get install lvm2
            sudo vgchange -ay
            sudo update-grub

---

### Post by oceola2 on 2015-02-01
@oldfred - I've removed some of the files installed in the list above as an experiment to see if it holds as there's no physical cluster.
Thanks for the input.

Commit Log for Sun Feb  1 14:49:53 2015
Completely removed the following packages:
clvm
libcmap4
libcorosync-common4
libcpg4
libdlm3
libqb0
libquorum5

The following were left to see if the change stays automatic.
libdevmapper-event1.02.1 (2:1.02.77-6ubuntu2)
lvm2 (2.02.98-6ubuntu2)
watershed (7) 						

Looking at the LVM as the system does not entertain MSWindows

---

### Post by oldfred on 2015-02-01
You cannot install Windows inside a LVM. 

Windows has its own proprietary logical partition scheme called dynamic partitions which of course does not work with Linux.

---

### Post by oceola2 on 2015-02-02
@oldfred - do not have Windows on this system and not trying to install it.

Problem initially was trying to get Ubuntu 14.04LTS and Ubuntu12.04.5LTS to "see" the LVM of Fedora21.
Had the same problem before with an earlier version of Fedora.
Just installed LVM2 and Watershed and Fedora now shows up in the Go/Computer for Nautilus

---

