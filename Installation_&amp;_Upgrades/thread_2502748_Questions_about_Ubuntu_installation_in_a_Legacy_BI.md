---
title: "Questions about Ubuntu installation in a Legacy BIOS PC ?"
date: 2024-11-27
forum: Installation &amp; Upgrades
---

### Post by elreydelaswasas2 on 2024-11-27
Type of partition, mount point, maximum recommended size, and labels for the root, boot and swap partition ?

---

### Post by deadflowr on 2024-11-27
What does non legacy bios mean?
Do you mean uefi mode?

There are no max size limits.
(Or limits are only restricted by the file system type used.
But having a 20TB boot partition would be rather ridiculous.)

Recommendations tend to go in the minimum size direction.
The sizes you need are going to be specific to your needs.

Though the boot should be at least 1GB these days, I guess.

Swap will depend on RAM and whether you hibernate or not, I assume that's still a thing.
I don't hibernate so I've not ever needed swap beyond the default size, which looks to be 2GB, but it's never eaten more than a couple MB.

I take no side on root sizes, since that's fairly specific to user needs.
But I'd say look at what Ubuntu's download pages system requirements says and use that as the minimum base size for root.

---

### Post by oldfred on 2024-11-27
If originally Windows 7 system, Ubuntu may be too much system.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

I use Kubuntu which is more of a mid-weight system on both newer & older systems.

If new user, best just to stay with / (root) as ext4 format.
It will by default create a swap partition. Unless a server type install or encription, you do not need /boot as separate partition.
Size depends a lot on how much data you will save in /home, and available drive size.
If very large drive smaller / & separate /home may be better, but also a bit more advanced.

I now suggest 35 to 40GB for / , but Ubuntu now uses snaps for many apps. Those can take a lot of space, saw one user who installed many snaps and the snaps alone were 20GB. My / on various systems with no snaps is from 10GB to 16GB but I also have all data in separate data partition.

---

### Post by ubfan1 on 2024-11-27
Any concern with a Windows install for dual boot?  Note that some Win 7 machines were fully UEFI capable (except for secure boot), even though the Windows install and partitioning was legacy. Switch to UEFI and GPT partitioning  might be considered. A Lenovo W520 (Originally 32 bit Win 7) was a 64 bit UEFI machine that ran fine in both modes.

---

