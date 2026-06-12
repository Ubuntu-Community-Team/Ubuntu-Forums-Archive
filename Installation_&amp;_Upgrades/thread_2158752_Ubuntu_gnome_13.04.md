---
title: "Ubuntu gnome 13.04"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by vonheed on 2013-06-30
I'm having problems with my install as there is no partition to select which is on both other laptops but not on my desktop, iget the same problem with any version I try to install. Thanks

---

### Post by Bashing-om on 2013-06-30
vonheed; Hi ! Welcome to the forum .

Not much info provided with which to help you with. Now-a-days installing another operating system CAN/may be rather complex. We now must consider GPT partitioning, if Windows is installed with dynamic partitioning, UEFI, ISRT.....older formatting schemes - still very much in use - limits the disk to only 4 primary partitions... and in this event one must make provisions/alterations.

So... show us what you are working with. 
From the liveDVD(USB) -> desk top -> key combo ctl+alt+t for a terminal interface:
Post back the out put of terminal commands:
```

sudo fdisk -lu 
sudo parted -l 
sudo parted /dev/sda unit s print

``` placed between code tags (#) from the top of the post ..for our readability.

Further advise pending those outputs.

[INDENT][INDENT]a tale in the telling[/INDENT][/INDENT]

---

