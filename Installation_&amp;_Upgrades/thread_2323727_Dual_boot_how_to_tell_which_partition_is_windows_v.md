---
title: "Dual boot: how to tell which partition is windows vs ubuntu?"
date: 2016-05-07
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2016-05-07
I am preparing to upgrade my windows 7 OS to windows 10.
I have Ubuntu installed as well and I select which OS using GRUB at boot.

I can't tell which partition has the windows OS vs Ubuntu? 
Once partition lists C:Acer (name of computer) and the other is D:home. I suspect C:Acer is where windows lives and I can install the new windows 10 OS there, but I'm not sure.

Is there an easy way to tell which partition has which OS?

Thanks

---

### Post by Impavidus on 2016-05-07
You can tell from the partition type. NTFS is Windows, ext4 or swap is Linux. But my guess is that Windows doesn't recognise the Linux partitions, so it doesn't give them drive letters. They should be visible in some sort of disks utility, although with limited information, as Windows doesn't know how to handle them.

Make sure you have backups of your documents in both Windows and Ubuntu before upgrading. Windows 10 is known to occasionally damage Linux partitions.

---

### Post by Bucky Ball on 2016-05-07
Further to that, once upgraded you may find you can only boot into Win10. There are fixes for it on the forum so have a sniff around if that happens. This seems to be a consequence of the upgrade.

---

### Post by oldfred on 2016-05-07
If Windows 7 is BIOS (most are) and Ubuntu is in logical partitions, backup partition table to text file and save to another device.
Many have upgraded and when Windows 10 rewrites partition table, it conveniently forgets to include the Linux partition. This has been a bug in Windows for years.

       Do not change partitions after you back this up, or it will revert to before changes.
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 

You do not want to get to the issue these users had:

 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[URL="http://ubuntuforums.org/showthread.php?t=1775331"]http://ubuntuforums.org/showthread.php?t=1775331
[/URL]
 Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462) 

[URL="http://ubuntuforums.org/showthread.php?t=1775331"]
[/URL]

---

### Post by michael351 on 2016-05-07
> **Bucky Ball said:**
> Further to that, once upgraded you may find you can only boot into Win10. There are fixes for it on the forum so have a sniff around if that happens. This seems to be a consequence of the upgrade.

... so I would lose the GRUB boot loader following a win10 upgrade? I had assumed that win10 would only install in the previous versions windows partition.
(if I had to - couldn't I just re-install Ubuntu w/Grub after windows10 install and get back my two OS's?)

---

### Post by yancek on 2016-05-07
With an MBR install, windows 10 will update boot files on the current windows partition and it will ALSO put new boot code in the master boot record.  A default windows system will not make any effort to detect any other operating system and always overwrites the code in the MBR.  You will not be informed this is going to happen and certainly will not be asked if you want it.  After upgrading to windows 10, you can  reinstall Grub with your Ubuntu DVD.  See the site below for methods to use.

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

Or you can download and use boot repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by michael351 on 2016-05-07
> **yancek said:**
> With an MBR install, windows 10 will update boot files on the current windows partition and it will ALSO put new boot code in the master boot record.  A default windows system will not make any effort to detect any other operating system and always overwrites the code in the MBR.  You will not be informed this is going to happen and certainly will not be asked if you want it.  After upgrading to windows 10, you can  reinstall Grub with your Ubuntu DVD.  See the site below for methods to use.

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

Or you can download and use boot repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Thank you !! It would not be the first time I have had to use Boot Repair!

---

