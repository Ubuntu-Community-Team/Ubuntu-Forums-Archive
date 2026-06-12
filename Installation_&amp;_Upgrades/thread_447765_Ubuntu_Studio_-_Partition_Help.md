---
title: "Ubuntu Studio - Partition Help"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by Hybride on 2007-05-18
I recently downloaded and burned the ISO of Ubunstu onto a DVD and it works fine. During the installation, I successfully managed to get up to the "Partitioning" part of the installation. I have only one 200GB hard drive on my computer and I have created a 25GB partition to install Ubunstu onto.

The problem is, the only option I have is to format the drive, thus deleting everything from it including my Windows XP and Windows Vista operating systems and all the files. I want to find a way to install it only onto the partition and not the drive.

Somebody recommended that I install Ubuntu 7.04 and install Ubunstu on top of it but surely there must be an easier way? Thanks for the help in advance.

---

### Post by mikewhatever on 2007-05-18
Don't you have manual partitioning option?

---

### Post by Hybride on 2007-05-18
> **mikewhatever said:**
> Don't you have manual partitioning option?
I do, and it shows the parition I want to use, but how do I tell it to install onto that partition? It just seems like an editor to me?

---

### Post by mpvano on 2007-05-18
If you're note sure what you're doing make sure you have the other partition backed up first (or that you don't care if you lose it by screwing up)...

- You usually will need TWO partitions to install Ubuntu, one for the OS, and one for swap.

- manually create a swap partition twice the size of your RAM memory
- make sure you've selected the option to USE it as swap. The manual partitioner has menu entry with choices for how to use the partition after you create it.
- manually create the ext3 data partition and select it's use as "/" or root (I can't remember which it says right now), in the same way

The partitioner summary should tell you that it's going to format the / and swap partitions and install the OS onto them.

If you get a choice to decide where to install Grub, think about installing it to the root partition (if it's a primary partition) and "activating" the boot flag so it boots from there. If you don't understand this or don't get a choice, don't worry about it.

The selections specifying how you want to use the partition determine where Ubuntu will be installed.

Sorry if this is a little vague, but it's hard to remember what the partitioner looks like and I can't run it right now to walk you through the choices more accurately - perhaps someone else can do that.

hope this helps a little...

Mario

---

### Post by mikewhatever on 2007-05-18
> **Hybride said:**
> I do, and it shows the parition I want to use, but how do I tell it to install onto that partition? It just seems like an editor to me?

Try following a guide [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu can not be installed on an existing partition which you want to keep. You need unallocated space for installation. In that space, at least two partitions (root,swap) must be created. 
Good luck.

---

