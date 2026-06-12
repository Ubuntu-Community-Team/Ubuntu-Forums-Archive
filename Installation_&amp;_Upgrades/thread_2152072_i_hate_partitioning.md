---
title: "i hate partitioning"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by paradive on 2013-06-06
is "use entire hard drive" not an option anymore?

---

### Post by hansdown on 2013-06-06
Hi paradive.

Most distros I've played with recently, recognise any system that is installed already, and ask

> replace (name of system) and install

---

### Post by paradive on 2013-06-06
> **hansdown said:**
> Hi paradive.

Most distros I've played with recently, recognise any system that is installed already, and ask

well, there **was**&#8203; a "replace Mint" option, but i screwed up the partitioning scheme there and need to start over.

---

### Post by Irihapeti on 2013-06-06
Assuming that you're working from an Ubuntu LiveCD, choose "something else" in the partitioning menu. Then you can set up your hard drive how you like.

For a single partition, remove everything that's already there and set up a new one. Or, you can boot into the liveCD, start GParted and do it from there, which gives you a gui.

---

### Post by hansdown on 2013-06-06
> **paradive said:**
> well, there **was**&#8203; a "replace Mint" option, but i screwed up the partitioning scheme there and need to start over.

If you're still in the partitioning stage, click the "back" button to get back there.

This will erase mint, and install to the entire disk.

---

### Post by paradive on 2013-06-07
> **hansdown said:**
> If you're still in the partitioning stage, click the "back" button to get back there.

This will erase mint, and install to the entire disk.

can you clarify a little? that's **EXACTLY **what i want to do. (ideally, I  would put /home on it's own partition, but i'm too dumb for that).

i tried deleting the set partitions with gparted so it would recognize a blank disc, but no go.

---

### Post by fantab on 2013-06-07
@paradive: Its never too late. Back Up all your DATA externally and Start Over. Using 'Gparted' from the LiveDVD/USB delete all the partitions that there are and create new partitions keeping in mind your needs. 

This is how I would do it:

/dev/sda1 25GB Primary Ext4 /
/dev/sda2 25GB Primary Ext4 'free for now' (in case you want to insall another distro or another Ubuntu version/flavor)
/dev/sda3 25GB Primary Ext4 'free for now' (in case you want to insall another distro or another Ubuntu version/flavor)
/dev/sda4 'All the remaining' GB EXTENDED
/dev/sda5 4GB Logical SWAP
/dve/sda6 'All the remaining' GB Logical Ext4 /home

---

### Post by cincinnatus13 on 2013-06-07
4GB is a LOT for swap, even with low RAM. But otherwise, doing something like the above could work for you. Just keep /home separate so upgrading/changing the OS won't affect all your docs, media, etc.

---

