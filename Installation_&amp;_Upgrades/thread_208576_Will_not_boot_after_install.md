---
title: "Will not boot after install"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by BrianK on 2006-07-03
rebuilding an old machine...  I just replaced the system drive.

I went through the desktop install.  Everything appears to go well.  I rebooted to load the installed os, but the computer stops after the harware checks (before any form of OS starts to load).  It's as if there's no bootable media, but I get no error messages.

I manually partitioned the drive.  I made 3 partitions, a 150MB /boot, a 240GB /, and a 2 GB /swap.

I noticed that none of the partitions were marked as bootable (after trying to boot several times), so I loaded up the CD & added the boot flag to the boot partition using fdisk.  Still can't boot.

My system has two PCI RAID cards, a SATA system drive (attached to the mobo directly) and a CDROM drive.  The system drive is seen as 'sdc'.  The two RAID cards are sda and sdb.  Grub's menu.lst shows that it's trying to find the boot image on hd(2,0) which sounds correct to me.  

Neither of the two RAID arrays have any data or partitions.

Any suggestions?

---

### Post by BrianK on 2006-07-03
So I downloaded ubuntu 6.06 server.  Now I can install & reboot.  Strangley enough, now my system drive is sda instead of sdc.  I'm guessing there's some issue with drive mappings with Ubuntu?

In any event, It gets to the point where it says "Loading Kernel" then after about 5 minutes says, /dev/sda2 does not exist & drops me to a shell.  This si the second machine this has happened to at my office.  What's the deal Ubuntu team?  What the heck am I paying you for?  oh wait... I'm not paying. ;)  well, a solution would be nice.

another oddity... Debian calls the system drive hda. ??

---

### Post by BrianK on 2006-07-03
So I may have found a bug...

I installed Debian on the machine & all went well.  As I saud, Debian sees the SATA system drive as hda instead of sda or sdc like Ubuntu.  Figuring there must be some sort of conflict or confusion on Ubuntu's part about the different sd's, I went out to Office Depot & bought a PATA hard drive.  Now Ubuntu sees the system disk as hda, and installs/runs fine.

I would report this, but don't know where to do it.

FYI: my RAID drives are configured, but not partitioned.  I don't know if this has anything to do with that or not.  The other machine this happened on also had two drives, the first had WinXP installed.

---

