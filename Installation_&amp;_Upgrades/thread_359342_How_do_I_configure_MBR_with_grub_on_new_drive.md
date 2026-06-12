---
title: "How do I configure MBR with grub on new drive?"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by eapache on 2007-02-11
I am running Ubuntu 6.10 and XP on a dual-boot with GRUB. I'm currently on an old 60GB hard-drive, and recently purchased a new 160GB drive. I would like to simply format the new drive with the desired partitions, and then image each partition over separately from disk a to disk b.

Because I have a larger drive, I am going to want to proportionally increase the size of my partitions to fill the new drive. My problem comes with the MBR of the new drive. I understand that the grub MBR just points to a disk sector where GRUB is stored. If I change the size of my partitions on the new disk, I can't copy the old MBR over because it would be pointing to the wrong spot.

I know XP has a 'fixmbr' command on the repair disk. Is there a similar utility that I could use for grub to properly configure my MBR, or would I have to install Ubuntu fresh after imaging over my windows partion and running a fixmbr from the windows cd?

---

### Post by Kateikyoushi on 2007-02-11
I think you can install grub from the live cd after you copied over the data to the new drive.
See this thread for detailed info. [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by eapache on 2007-02-12
Thanks, that looks like it will work. I'll give it a shot.

---

