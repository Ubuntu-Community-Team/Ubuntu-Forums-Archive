---
title: "Windows 8.1 and Ububtu 14.04.3 LTS Partition"
date: 2015-11-02
forum: Installation &amp; Upgrades
---

### Post by john472 on 2015-11-02
I've been seeing a constant spinning wheel for over 24 hours after clicking continue in the partition menu. Is there anyway to see what is causing the long process or should I reboot and start over? Clicking back doesn't work as the field is greyed out after it started the process.

---

### Post by yancek on 2015-11-02
You will need to be considerably more detailed to get any help.  Partition menu of what?  Are you using GParted to try to modify your partitions?  Is it installed to the system or are you using in on a CD/DVD/flash drive?  What are you trying to change by "clicking continue on the partition menu"?

---

### Post by oldfred on 2015-11-02
Windows or Ubuntu should not be hard rebooted. Best to try to close applications and do a normal shutdown.

With Ubuntu you want to remember the elephants.
       Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

Is error from using Windows to resize its own NTFS partition? That is the correct way to make space for Ubuntu partitions. And you must have fast start up (hibernation) off in Windows.
Details in link below for UEFI installs.

---

### Post by john472 on 2015-11-02
The partition menu is from the Ubuntu GUI installer after selecting "install Ubuntu" in grub and then selecting dual boot option to keep the master boot record to boot both the existing windows 8.1 and the Ubuntu. The partition option was to reduce windows on fat32 so as to make room for the Ubuntu install

---

### Post by oldfred on 2015-11-03
Only use Windows to shrink Windows NTFS partitions. And reboot immediately so it can run chkdsk.

What FAT32 partition do you have? Only the ESP - efi system partition which with Windows is typically a  100MB should be FAT32.

Post this:
sudo parted -l

---

