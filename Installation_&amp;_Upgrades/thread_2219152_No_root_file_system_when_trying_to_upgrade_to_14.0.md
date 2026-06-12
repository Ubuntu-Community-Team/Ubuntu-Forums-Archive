---
title: "No root file system when trying to upgrade to 14.04"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by tleon996 on 2014-04-23
Presently, I am running 12.04 lts in a dual boot with Windows 7 with Ubuntu installed on a seperate 100G ext4 partition. I am trying to upgrade to version 14.04 using the live DVD. When I boot the DVD and select install, the first screen shows everything OK, next when presented with the choice of erasing the entire disk, etc. I choose the something else because I do need to keep Windows alive for a few things. It then takes me to a display of the partition table of my disk, I select the existing partition where I have my existion version 12.04. I then get the error, "no root file system defined, please correct in partitioning menu". What's going on here? There has to be a root file system defined for ver. 12, what am I missing?

Thanks for any help...

---

### Post by fantab on 2014-04-23
You have to choose the **MOUNTPOINT '/'** when setting up the root partition or '/home' when setting up a home partition or whatever.
If you want to completely install clean and fresh then select '**format**'... if not then you will upgrade the existing install. I always do a clean install when I need to upgrade.
**Use as=Ext4 journaling system**.

---

### Post by jaygee2 on 2014-04-23
I am in a similar position. I have an elderly GX620 which is running Win7 on an 80 GB HD. I have added a second HD to allow linux (same size) and when I get to the point of partitioning I choose something else as I really dont want to risk loosing Win7. At this point I get the same message "no file system etc"
I have tried to set up the drive using Parted Magic (added /root and /home also a swap) but the install wants to use the origional disk. I am trying to install Ubuntu 12.04.3 on the second HD.
Any help would be appreciated.

---

### Post by 3rdalbum on 2014-04-23
As Fantab posted an hour earlier, on the Something Else screen you need to set your Ubuntu partition's mount point to /

NOT in any other piece of software, but in the Ubuntu installer.

---

### Post by jaygee2 on 2014-04-23
OK, Took the bull by the horns and the install went ahead seemingly succesful. Reboot, straight into Win7, no ubuntu. So what next.
I put the / in sdb so I need to link to sda to get grub to give me an option. How To required.

---

### Post by oldfred on 2014-04-23
With Something Else or manual install on the partition screen is also the combo box at the bottom for location of boot loader. It defaults to installing into sda, but if you have more than one drive you want to install grub to the same drive as Ubuntu and then set BIOS to boot from that drive. If Windows is on the other drive keep the Windows boot loader on the Windows drive, but you will only use it if you have issues.

I have partitions created in advance, so I click on change to get the popup for selecting / & formatting. If you have unallocated space and adding a new partition then use +.
Shows combo box. My examples are over installing on a partition on sdc or sdd, but default for boot loader is still sda.

---

### Post by tleon996 on 2014-04-23
Got it upgraded, but now I cannot print, but that's a topic for a different thread...

---

### Post by jaygee2 on 2014-04-24
Thank you all for the suggestions, unfortunately I could not make it work. I will shelve the job for the future or untill  I find out more.
I wish to have two separate installations on different HDs but it seems beyond my capabilities. Going on the back burner for now.
Again thank you.

---

### Post by fantab on 2014-04-24
> **jaygee2 said:**
> Thank you all for the suggestions, unfortunately I could not make it work. I will shelve the job for the future or untill  I find out more.
**I wish to have two separate installations on different HDs **but it seems beyond my capabilities. Going on the back burner for now.
Again thank you.

You must always start a new thread clearly describing your situation and your aim.

It is quite easy to install dual or multi-boot from different HDDs.
The process is same, you will choose 'Something Else' option at the Installation type dialog during install and set up partitions as suggested:
Use as = Ext4
Mountpoint = / or /home or etc
format = yes...

Do you have UEFI or BIOS?

---

