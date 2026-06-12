---
title: "Replaced Win 7 with Ubuntu 11.10, doesn't recognize my NTFS drive"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by soroushar on 2012-01-16
Hey guys, first I have to say that I am completely new to Ubuntu and linux and such...a total noob
I replaced win 7 on my laptop with ubuntu. I had 2 drives on my hdd and formatted one of them to ext4 and made a partition for swap. the other drives contains all my docs and media and is still NTFS. Ubuntu installed without any errors and I installed all the updates. The ntfs drive doesn't show up now. I opened up disk utility and it shows the other drive as unknown.
I downloaded ntfs-3g and tried installing it by typing './configure; make; make install' but the last command gives a permission error.

anyone know what should I do?

oh, and btw its an Acer 5738z and the 64-bit version

---

### Post by jroa on 2012-01-16
Try sudo before the command.  This will give you the privileges you need.

```
sudo make install
```

---

### Post by oldfred on 2012-01-16
Ubuntu comes standard with all the NTFS drivers you need. You should not have to recompile and may confuse things if you do.

As long as you have a NTFS partition you will need a copy of Windows repairCD or USB to run chkdsk. Ubuntu runs fsck every 40-60 reboots, but cannot run chkdsk. And if you have any corruption, Ubuntu will not mount a NTFS partition until you have run chkdsk.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by soroushar on 2012-01-16
> **jroa said:**
> Try sudo before the command.  This will give you the privileges you need.

```
sudo make install
```

thanks for the quick reply. it did install. now I can't figure out how to mount it or set ubuntu to mount the drive at boot.

what should I do now?

---

### Post by soroushar on 2012-01-16
> **oldfred said:**
> Ubuntu comes standard with all the NTFS drivers you need. You should not have to recompile and may confuse things if you do.

As long as you have a NTFS partition you will need a copy of Windows repairCD or USB to run chkdsk. Ubuntu runs fsck every 40-60 reboots, but cannot run chkdsk. And if you have any corruption, Ubuntu will not mount a NTFS partition until you have run chkdsk.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

thanks, although I don't have a repairCD at hand but I do have the installation disk, can I run chkdsk from there? cuz it takes too much to create a repaircd

---

### Post by oldfred on 2012-01-16
If you have a full install DVD, it can run the Windows repair console. But if it is just a Vendor recovery that is an image of the hard drive the vendor shipped it can only write the image back to the drive.

Any friends with the same 32 or 64bit version of Windows can make the repairCD.

We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Another download site Despotism Believed to be ok.
[http://ubuntuforums.org/showpost.php?p=11249721&postcount=439](http://ubuntuforums.org/showpost.php?p=11249721&postcount=439)
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links (Now $10.00):
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Mark Phelps on 2012-01-16
I used to think this was entirely an NTFS problem, then I started seeing threads here where folks did NOT have ntfs-3g installed.

Seems that, in 11.10, ntfsprogs is installed by default -- and that conflicts with ntfs-3g (which, then, is NOT installed).

Try removing ntfsprogs and installing ntfs-3g.  See if that then allows you to mount the NTFS partitions.  

Many have reported success with this simple change.

---

### Post by soroushar on 2012-01-16
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

this tutorial worked.
thanks to all those who replied :cheers:

---

### Post by oldfred on 2012-01-16
Ubuntu does not always have the newest version but they have merged NTFSprogs & NTFS-3g.

[http://phoronix.com/forums/showthread.php?45397-NTFS-3G-Merges-With-NTFSprogs-Plus-New-Version](http://phoronix.com/forums/showthread.php?45397-NTFS-3G-Merges-With-NTFSprogs-Plus-New-Version)

This says they may conflict.
[http://askubuntu.com/questions/68208/ntfsprogs-uninstalled-ntfs-3g-package](http://askubuntu.com/questions/68208/ntfsprogs-uninstalled-ntfs-3g-package)

---

