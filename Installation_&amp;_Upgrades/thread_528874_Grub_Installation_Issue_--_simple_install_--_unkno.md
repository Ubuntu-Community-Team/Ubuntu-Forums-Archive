---
title: "Grub Installation Issue -- simple install -- unknown problem"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by NdJ on 2007-08-18
Hi,

Here's hoping someone can help me work out a grub problem I'm up against -- first with the background.

** Ubuntu 7.04 server amd64
** New Dell 2950 using PERC RAID5 (5 drives + 1 hot spare) -- provides 2TB usable space
** First partition is a 32GB swap
** Second partition is a ~2TB ext3 partition for the / mount point (not too bothered with LVM etc -- just trying to get the thing to work at this stage)

The problem I run into with the standard installation process is that when it gets to the stage of installing grub if fails with:-
""
[red screen] Unable to install grub in (hd0)
""

When I then attempt to run the grub-install tool manually I get:-
""
# grub-install /dev/sda
The file /boot/grub/stage1 not read correctly.
""

The stage1 file does exist however.

I've attempted to do a grub-install --recheck /dev/sda without success.

My /boot/grub/device.map file maps:-
(hd0) /dev/sda

Thoughts, suggestions, advice greatly appreciated.

N

---

### Post by NdJ on 2007-08-19
Found a work-around for the issue in the end -- the ~2TB partition was the culprit -- breaking my partitions up into allocations less-than 2TB allowed the install to complete normally.

I was clearly up against the ~2TB limit for grub/fdisk (or something) -- can't imagine why grub would inherit a 2TB partition limit issue, but either way my issue is now resolved.

N

---

