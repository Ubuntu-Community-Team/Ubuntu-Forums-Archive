---
title: "Install partitioning problems"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by Paraparaumu on 2007-03-18
I'm trying out Kubuntu, coming from Mandriva. It looks like I've already hosed my notebook's partition table in the attempt to install Kubuntu while maintaining some of my existing partitions. I started by booting from the DVD, and mostly liked what I saw so tried doing the install. I selected "Manually edit partition table", and then problems began.

First off, I like using ReiserFS for my /usr and /home partitions, since AFAIK ReiserFS is the only journaling FS that allows for deleted file recovery. Unfortunatly, ReiserFS is not an option for the Kubuntu install partitioning editor. I  first tried keeping my existing ReiserFS partitions in place while converting some of the other partitiions, but that didn't work out the way I wanted - and when I chose "Go Back" from the "Prepare mount points" step to revise some of my partitioning choices, I found that I'd lost an encrypted partition when the installer apparently merged it into adjacent free space.

From experimenting, it looks like I need to actually delete and then recreate the partitions in the "Prepare partitions" step in order to reliably make use of them in the "Prepare mount points" step. If I don't delete and recreate them I seem to get all kinds of random partitions showing up in the lists. Even when I do delete and recreate them the partition number and identifiers in the "Prepare mount points" step don't match what I had in the "Prepare partitions" step, meaning I have to cycle through the choices until I find a match by size with the partition I was expecting to use for a particular mount point.

Then when I finally had the partitions the way I wanted them (I think), I advanced past the "Prepare partitions" screen - and then tried going back, since the screen that listed the partitions to be formatted only used the arbitrary (and apparently inconsistent hdaXX partition identifiers), and I wanted to make sure I hadn't accidentally set it to reformat a partition I wanted to keep. The "Prepare partitions" screen was empty, so I tried going ahead again - and got "The advanced partitioner (qtparted) crashed..."

I also get the message "The partition assigned to '/' is too small (minimum size: 2048 Mb)." despite having separate /usr, /home, and /var partitions defined. Why?

I'm going ahead and trying (K)Ubuntu anyway, but this partitioning mess has certainly been a horrible start.

---

### Post by zvacet on 2007-03-20
Ubuntu need more space for root partition(5 or more).I didn´t understand do you want to keep your Mandriva or not?if you don´t delete it and install Ubuntu in ext3 format.

---

### Post by jtholmes on 2007-03-21
I dont know what version/build of Kubuntu u have but there
is a bug in the Installer at or before  id  20070317  current.

The crash was fixed in 20070320. The reiserfs may still be a problem
20070321 is not out yet but give it a try when they release it later
today.

---

