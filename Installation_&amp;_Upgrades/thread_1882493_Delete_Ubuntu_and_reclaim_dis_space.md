---
title: "Delete Ubuntu and reclaim dis space"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by Enigmaman on 2011-11-17
I have Ubuntu 10.10 installed on my  partitioned hard disk on mt Dell Dimension 5000 alongside Windows XP on a separate partition. They were formerly on a dual boot via GRUB. 

I recently did a clean install ox XP and found that GRUB disappeared and it booted straight into Windows. Now Windows is getting very short of space and I would like to delete Ubuntu and reclaim the disk space.

Can anyone advise please? Bear in mind that I would have to boot Ubuntu from the live CD.

Thanks in adbance.

---

### Post by dniMretsaM on 2011-11-17
You could just restore GRUB. See [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by TBABill on 2011-11-17
You just need a partition program to delete the Ubuntu partition and then resize the Windows partition to claim the space Ubuntu was using. Just make sure you don't delete your other Windows partitions.

---

### Post by oldos2er on 2011-11-17
> **Enigmaman said:**
>  Bear in mind that I would have to boot Ubuntu from the live CD.

I don't see why. Since Windows' boot loader is up and running you can simply delete the Ubuntu partition from within Windows, as TBABill said.

---

### Post by Mark Phelps on 2011-11-17
A good, free, partitioning tool available for Windows is Partition Wizard.  Suggest you download and install that, and use that to remove the partitions.  

You might have to burn the CD boot version and boot using that if you want to then extend your existing Windows partition.  Vista and Win7 have a tool (Disk Management utility) that would let you do that without having to boot from CD, but that tool wasn't available with XP.

---

