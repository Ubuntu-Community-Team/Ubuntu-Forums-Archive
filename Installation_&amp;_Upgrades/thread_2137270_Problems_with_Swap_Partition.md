---
title: "Problems with Swap Partition"
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by jworks on 2013-04-20
Hi. Yesterday I did a fresh install of xubuntu on my notebook. I created a new partition table, and 4 primary partitions (boot, swap, root, home).

After restarting the swap partition was showing as Unkown in gparted, so I booted again from USB, formatted the partition to linux swap, and selected swapon. Now the partition was showing as linux-swap in gparted, but it's not being used. The command free -m shows available swap, but 0 used, and the hibernation option is greyed out. After another reboot it shows 0 available swap, hibernation option is gone, but I can still find the partition in gparted as linux-swap.

Then I followed instructions for fixing broken swap partition I found:
```
[INDENT] sudo swapoff -a
sudo cryptsetup remove /dev/mapper/cryptswap1
sudo gedit /etc/crypttab
[/INDENT]
Remove the SWAP line (e.g.[COLOR=#e69138] /dev/sda2[/COLOR])[INDENT] sudo /sbin/mkswap [COLOR=#e69138]/dev/sda2[/COLOR]
sudo swapon [COLOR=#e69138]/dev/sda2[/COLOR]
sudo gedit /etc/fstab 
[/INDENT]
Replace /dev/mapper/cryptswap1 with [COLOR=#e69138]/dev/sda2[/COLOR].
sudo ecryptfs-setup-swap


```
After this free -m shows available swap again, but 0 used. hibernation option is back but greyed out again.

cat /proc/swaps returns this
```
Filename                Type        Size    Used    Priority
/dev/dm-0                               partition    4001788    0    -1

```
Im not sure why it shows /dev/dm-0 instead of /dev/sda2.

Im still a beginner but I really want to get this right.
Any help or tips are much appriciated.

---

### Post by oldfred on 2013-04-20
Did you encrypt /home?

If so then swap is also encrypted and gparted then cannot see it. So it was correct.

When you recreated it, it had a new UUID, so you have to update fstab with the new UUID.
But then I do not know if with encryption it goes back and encrypts or not?

---

