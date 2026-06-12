---
title: "How to deinstall Ubuntu?"
date: 2016-04-12
forum: Installation &amp; Upgrades
---

### Post by nescio2 on 2016-04-12
Hi! Recently I purchased a new notebook. It has both a SSD and a HDD. Windows 10 is preinstalled on the SSD. I installed Ubuntu 14.04 on the machine. However, after I installed it, I realized it was installed on the HDD (which I intended to leave empty for the moment) instead of on the SSD (where I had intended Ubuntu to be). Therefore I now want to completely remove Ubuntu (from the HDD) and install a fresh version on the SSD (to have a dual boot system on one and the same drive). How to uninstall Ubuntu?

---

### Post by ajgreeny on 2016-04-12
You may manage by simply reinstalling the second Ubuntu onto the SSD, then removing the first Ubuntu partitions using something like gparted from a live system.  Do not remove the partitions first as you may then find that you can not boot either OS.

I think you must be very careful about the way you do this as it will depend upon what happened to your Windows boot files, whether the machine is using UEFI or MBR/BIOS, and what partitions you have where on the two disks.  The safest way to proceed now is probably to run the **Boot-info script** from **Boot-Repair** in my signature, which will give you a pastebin link to show us which will have all the info needed to suggest your best course of action.

---

### Post by nescio2 on 2016-04-23
Thank you for your reply.
Today I've installed a fresh new version of Ubuntu. However, it simply replaced the old version (on the HDD), instead of being installed alongside the existing operating systems (on the SSD).
Now, how do I completely remove Ubuntu (from the HDD)?

---

### Post by lisati on 2016-04-23
Please post the output from the [boot-info]("https://help.ubuntu.com/community/Boot-Repair") script, as requested by ajgreeny. This will help us guide you through the process.

---

### Post by nescio2 on 2016-05-02
Hopefully this is the what you've been asking for:

[http://paste2.org/8hB0ILnG](http://paste2.org/8hB0ILnG)

Now, how to proceed?

---

### Post by yancek on 2016-05-02
Your bootinfoscript output show "one" drive of 465GB.  Where's the SSD?  You have three windows partitions on the 465GB drive and you have one Linux partition plus a swap partition.
Which installation option did you select when booting the Ubuntu installation media?  You need to use the manual "Something Else" option so you have control over where to install. Installers don't read minds and it won't install where you "want" it to go because it has no idea where that is unless you tell it.  You can do that with the manual method.  Generally it will look for the largest unallocated or free space to install to.

If you had windows 10 pre-installed, it was likely a UEFI install so you need to boot Ubuntu UEFI and install it with that mode for both systems to work.
You have an EFI partition but there are no EFI files shown for windows or Ubuntu.  Are you currently able to boot either system?

Just to clarify, you do not uninstall operating systems, you simply format the partition on which they reside and then re-use that partition.

---

### Post by nescio2 on 2016-05-05
The SSD is called "nvm0n1", which is 512 GB=477 GiB; this is the primary drive.
The HDD is called "sda", which is 500 GB=466 GiB; this is the secondary drive, which I intend to use a back-up.
In reply to your remarks, as far as I understand it, the situation is as follows:
- the boot manager is located on nvm0n1p1
- Windows 10 pre-installed on nvm0n1p3 (with nvm1n0p4 as WinRE_DRV)
- Ubuntu 16 currently on sda4 (with sda5 as swap)
- sda2 is called Data, which is by far the largest partition; it is accessable from both Windows and Ubuntu, but currently as good as empty
- nvm0n1p2 and sda3 are tiny partitions; I'm not sure what they're used for, but I guess the former is related to Windows, the latter to Ubuntu.
And yes, both systems run; I'm using Windows 10 on this machine weekly, and Ubuntu 16 daily; no problems with booting.

Yes, I did select the "something else" option when reinstalling Ubuntu, of course. However, although I did try to select a different partition, unfortunately the install manager refused to accept any other partition than the one where it has detected the (previous) version of Ubuntu.

Thank you for your clarification. Now, how do I format the partition on which Ubuntu is currently located?

---

### Post by ubu_dynamite on 2016-05-05
I would just make room on the nvme0n1 ssd install ubuntu to that free space and if everything is working delete the old ubuntu installation by deleting the partition with disks or gparted.
After that run "update-grub" to remove the old installation from grub.

---

### Post by nescio2 on 2016-05-15
Could anybody explain in more detail how to delete partitions? "gparted" has been mentioned, however, I don't have any experience with it, and I'm a bit reluctant to start experimenting with something powerful when accidental mistakes can not easily be reverted.

---

