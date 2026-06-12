---
title: "Updating Dual Boot Installation (2x HDDs)"
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by samn122 on 2013-08-07
Hi everyone, I currently have a dual boot setup of Windows Vista on a 500GB HDD and Ubuntu 9.10 on my second 300GB HDD. I'm looking to upgrade the 9.10 to 12.04 through a USB installation but the problem is that GRUB2 is on the 500GB HDD with Windows Vista. **My plan is to format the 300GB HDD and install 12.04 on that but I think it might be problematic. **Currently the 500GB HDD boots first in order to get to the GRUB2 bootloader but if the 300GB HDD boots first I get nothing (black screen with blinking cursor). GRUB2 is on the HDD with Windows Vista and won't be affected by formatting the HDD with Ubuntu. I think this is a pretty weird situation and any help would be appreciated!

---

### Post by Mark Phelps on 2013-08-07
When you installed 9.10, you likely had BOTH drives connected and GRUB, by default, installs to the "first" drive it sees -- which was most likely the Vista drive. You can't boot the "Linux" drive because GRUB is not installed there.

What I would do is the following:
1) Disconnect the Vista drive
2) Install 12.04, including GRUB
3) Reconnect the Vista drive -- but continue to boot from the 12.04 drive
4) Open a terminal in Ubuntu and enter "sudo update-grub".  This will regenerate the GRUB config file and should add an entry for Vist.

When you then reboot (still from the Ubuntu drive), you should see a GRUB menu with entries for Ubuntu and Vista.

---

### Post by oldfred on 2013-08-07
I would add to Mark Phelps suggestions and install the Windows boot loader to the Windows drive. You still boot from the Ubuntu drive and if will still offer to boot both, but if Ubuntu drive stops working, you then can directly boot Vista. The grub on the Vista drive has to find the rest of grub and menu on the Ubuntu drive so if that drive fails, you would not be able to boot Vista.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

If you do not disconnect Windows drive you have to use Something Else or manual install to get the option to install the grub2's boot loader to the second drive. All installs default to sda and only manual install gives an option to change location.

 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by samn122 on 2013-08-07
Thank you both for the replies! The fix was actually simpler than I thought. After formatting the 300GB drive and installing 12.04 (and the bootloader) I was able to boot into GRUB2 and then either Vista or Ubuntu. If I have any future problems I'll be sure to refer back to this thread. Thanks again!

---

