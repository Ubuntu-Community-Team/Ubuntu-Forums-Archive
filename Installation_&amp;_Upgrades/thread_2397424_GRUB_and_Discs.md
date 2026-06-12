---
title: "GRUB and Discs"
date: 2018-07-29
forum: Installation &amp; Upgrades
---

### Post by hipkat2 on 2018-07-29
Somehow, when I first reinstalled Ubuntu as a dual boot w/Win 10 on a 500GB HDD dedicated for Linux, on a new build in January, I did some dumb things. For one, my startup screen looks like this and I really don't want to screw it up by editing it.

Second my partitions are not right. Seems like I have them sized/labelled wrong?? 

I could just reformat the drive and start over, but that GRUB/MBR scares me that I'll lose the ability to boot into Windows

---

### Post by oldfred on 2018-07-29
You are showing multiple drives.
The one you posted shows an extended partition which is MBR.
But you also show a 4GB drive which has to be gpt partitioned.
Is system UEFI or older BIOS only system.
And is Windows installed in UEFI or BIOS boot mode?
Windows only boots from MBR with BIOS.
Windows only boots from gpt with UEFI.

Post this above in first post:
sudo parted -l

Grub only boots other systems installed in same boot mode, either both must be UEFI or both must be BIOS. If newer UEFI system you can, only from UEFI boot menu,  boot systems installed in mixed boot mode.
And grub only boots working Windows. So when Windows does updates and turns fast start up back on grub will not boot it. So best to have way to directly boot Windows. UEFI will always give that option. If BIOS/MBR you can install different boot loaders in each drive. Or have Windows boot loader in Windows drive and Ubuntu boot loader on Ubuntu drive. If drive is gpt, you have have an ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot. I always have both as first two partitions on all gpt drives.

---

### Post by hipkat2 on 2018-07-29
> **oldfred said:**
> You are showing multiple drives.
The one you posted shows an extended partition which is MBR.
But you also show a 4GB drive which has to be gpt partitioned.
Is system UEFI or older BIOS only system.
And is Windows installed in UEFI or BIOS boot mode?
Windows only boots from MBR with BIOS.
Windows only boots from gpt with UEFI.

Post this above in first post:
sudo parted -l

Grub only boots other systems installed in same boot mode, either both must be UEFI or both must be BIOS. If newer UEFI system you can, only from UEFI boot menu,  boot systems installed in mixed boot mode.
And grub only boots working Windows. So when Windows does updates and turns fast start up back on grub will not boot it. So best to have way to directly boot Windows. UEFI will always give that option. If BIOS/MBR you can install different boot loaders in each drive. Or have Windows boot loader in Windows drive and Ubuntu boot loader on Ubuntu drive. If drive is gpt, you have have an ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot. I always have both as first two partitions on all gpt drives.
That's one physical drive, the partitions are just goofy. I want to just reformat it and start fresh as for the MBR, it's UEFI. Brand new computer and fresh install of Win 10. In this screenie of the Windows Disk Management tool, Drive 2 is the 500GB HDD that Linux is installed on. It seems that Ubuntu is using the 10Gb partition for /Home which was supposed to be /swap, because if I try to update to 18.04, it says the drive is full and I just got a popup showing my 10Gb /home partition is full and needs to be cleaned out. 

So a better question is can I change how those partitions are assigned in Ubuntu's disc manager?

---

### Post by hipkat2 on 2018-07-29
Yeah, this is bizarre

---

### Post by oldfred on 2018-07-29
Screenshots are too small for my old eyes.
And Windows does not show Linux partitions well.
Better to use gparted if gui or command line to really show details.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by hipkat2 on 2018-07-29
Ugh, sorry about that, I didn't look to see how low res the images were. See if this is better

Never mind, the forum is scaling it down. Use the link, instead

[IMG]http://i65.tinypic.com/vyy7ol.jpg[/IMG]

---

### Post by hipkat2 on 2018-07-29
....

---

### Post by oldfred on 2018-07-29
Those are standard partitions with BIOS/MBR configuration on sdc.
Root is small and almost full. I normally use 25GB and do have all data in other partition(s).
Little key icons, so those partitions mounted. You can only edit from gparted on live installer and may have to unmount or swapoff the swap partition.

---

### Post by hipkat2 on 2018-07-30
Well, for some reason, Ubuntu wouldn't boot anymore, it was hanging on bootup so I did some research and found dualbootrepair, which restored the original Windows MBR. Now I can reformat that drive and reinstall. Thanks for the help you offered!

---

