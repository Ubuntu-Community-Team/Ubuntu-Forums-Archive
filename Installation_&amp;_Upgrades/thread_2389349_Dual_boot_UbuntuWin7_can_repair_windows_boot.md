---
title: "Dual boot Ubuntu/Win7 can repair windows boot"
date: 2018-04-15
forum: Installation &amp; Upgrades
---

### Post by JimLS on 2018-04-15
Having trouble making dual boot.  Disconnected second SATA drive since it will only be for data and not involved in install.  Formated the SSD with first partition as NTFS and second as Ext4 and marked first as boot with gparted.  Then loaded win7 on first partition.  Loaded Ubuntu on second and created additional swap.  I ran windows 7 DVD to repair boot.  Then Ubuntu with boot repair.  Grub shows windows but when I select it I get a message that it isn't bootable.  I have been through windows and grub repair a couple of times but no luck.  Here is the boot-repair info

[http://paste.ubuntu.com/p/CFGRRfjZN7/](http://paste.ubuntu.com/p/CFGRRfjZN7/)

---

### Post by yancek on 2018-04-15
>   I ran windows 7 DVD to repair boot.

Not sure why you did that.  When installing Ubuntu and the Grub bootloader, it almost always detects windows and when you reboot after install you should have a windows option.  Did that not work for you? Your boot repair shows you have a Legacy install with Grub code in the MBR pointing to the Grub boot files on sda2 which have correct entries for Ubuntu and windows and the correct windows boot files on it's partition so I don't know why they won't boot.  Does Ubuntu boot?

---

### Post by JimLS on 2018-04-15
Yes.  Ubuntu boots.  No issues with Ubuntu that I know of.  I am typing this on it.

Initially the grub bootloader did not show the windows install.  That's why I ran windows boot repair.  It said it found issues (not sure what exactly).

Should I just start over?  Do I need to remove grub from the MBR when I start over?  This was basically a restart of a problem I had trying to install these and win10 and had two disks.  Was trying to simplify it...

I used gparted to set up the partitions and think grub was still in the MBR.  Perhaps that was the issue?  If I restart the whole install how should I make sure the MBR is clean?  Or do I not need to worry about it?

---

### Post by yancek on 2018-04-15
If the windows you want to boot is the one on the first partition of the drive on which you have Ubuntu, I don't see where the problem is.  Grub in the MBR, correct grub entries in it's menu for both windows and Ubuntu and the correct boot files show for both systems.  It should boot.  

Your windows filesystem might be corrupted.  If you have a windows DVD, you might try booting it and running chkdsk.  Can't think of anything else which could cause this.

---

### Post by JimLS on 2018-04-15
From the Win7 install disk I went to repair and command line.  Then ran:
bootrec.exe /FixMbr
bootrec.exe /FixBoot
Windows7 then booted and did some initialization that didn't run before for some reason.  Name of user, name of pc, etc.  Then windows was working.  Then ran boot-repair in ubuntu (from live CD after installing boot-repair).  Both booted but mouse didn't work in windows for some reason although it had worked previously and with install media.  Changed USB3.0 from 'smart auto' to 'auto' in bios.  Then loaded drivers from motherboard disk.  That restored network connection among other things.  All seems to be working.

---

