---
title: "Preinstalled windows is not available"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by bavi on 2008-10-19
HI,
After I installed latest ubuntu on the same partion as windows xp, I cannot start windows.  No option for windows on the menu.  How can I access windows xp?

thanks,

---

### Post by oldos2er on 2008-10-19
Did you install using Wubi, or the Live CD?

---

### Post by bavi on 2008-10-20
Installed from window by clicking the first option (install along with windows). I selected the guided - use entire partion to install.

---

### Post by deGz0rx on 2008-10-20
i think you installed ubuntu over XP
maybe theres a way to revert this but im not sure

lol buddy, you shouldhave been more careful
:(

---

### Post by Ryadt on 2008-10-20
It looks that you wiped windoze out. Can you post the output of```
sudo fdisk -l
```

---

### Post by posburn on 2008-10-20
Yep - if you selected your existing XP partition and then "use entire partition" the install will do just that.  It wiped your XP partition.  Sorry, this is irreversible AFAIK.  Hope you had backups of your important data.

---

### Post by Kevbert on 2008-10-20
Unfortunately, you've lost Windows. If you want to run windows and Ubuntu you need to install Windows first (when you do this make a spare partition of 10GB or more for Ubuntu). When you decide to install Ubuntu you should select manual install and remove the second partition (for Ubuntu). Now set up a Swap partition of twice your ram memory size (for memory overrun and hibernation), and another partition using the remaining hard disk, mounted / and formatted ext3 (for the Ubuntu system).  Once the install is complete you'll get the grub menu which gives the option whether you want to boot into Ubuntu or Windows.

---

### Post by bavi on 2008-10-20
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11796    94751338+  83  Linux
/dev/sda2           11797       12161     2931862+   5  Extended
/dev/sda5           11797       12161     2931831   82  Linux swap / Solaris

---

### Post by bavi on 2008-10-20
I've to recover windows.  atleast my documents.  how can I do that?  any software to recover the data?

---

### Post by Kevbert on 2008-10-20
Check in your computer manuals if you have a hidden partition for re-installing Windows...
Unfortunately Ubuntu has overwritten your windows partition, so you've lost your files.  Windows won't recognise the linux partitions so you'll need to run up the Ubuntu CD and use the partitioning software to set the drive to Windows NTFS. Go to System-Administration-Partition Editor to run Gparted.  Select each partition that is displayed in turn and delete it. Create a new partition using half the hard disk and format it ntfs (for windows). Now you should be able to install Windows. If you don't have the original Windows CD and haven't had the PC long you may have to ask the supplier nicely to re-install Windows.
I can't stress enough times that you should back up all important data.
Good luck.

---

### Post by bavi on 2008-10-20
heard about [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) or their TestDisk software? which one for ubuntu?

---

### Post by Kevbert on 2008-10-20
Never tried it. Thanks Bavi for the link. If you have any luck with it let me know.  I know that security services can recover any data from a hard disk regardless of how many times the disk has been written to.  The only way to be 100% secure is to physically destroy the hard disk platters but that is a little extreme.
You want the Linux kernel 2.6.x i386/x86_64, tar.bz2 version.

---

### Post by az on 2008-10-20
> **bavi said:**
> I've to recover windows.  atleast my documents.  how can I do that?  any software to recover the data?

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

You need another drive onto which you will store the recovered data - you cannot recover it "in place".

---

### Post by jazzcommunication on 2008-10-20
yep you lost it all, :( except for gaming...you can reinstall your windows later in Sun's Virtualbox 2.0 or vmware player, then run your windows inside linux without booting....next time please take the time to read and understand what is on the screen.... and store your important data on an external hd before big changes like this....

---

### Post by bavi on 2008-10-21
> **Kevbert said:**
> Never tried it. Thanks Bavi for the link. If you have any luck with it let me know.  I know that security services can recover any data from a hard disk regardless of how many times the disk has been written to.  The only way to be 100% secure is to physically destroy the hard disk platters but that is a little extreme.
You want the Linux kernel 2.6.x i386/x86_64, tar.bz2 version.

I'm new to Ubuntu.  Please help me to install the software.  I've downloaded on my desktop and extracted to a folder on desktop.  then what?

---

