---
title: "Windows 8.1 wiped out post-dualboot Ubuntu installation attempt"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by jefersen on 2013-12-13
So I've been meaning to  try  Ubuntu for a while now, and finally manned up and attempted to  dual boot it with Windows. I did it - except that it seems like I've  lost Windows 8 completely (yeah, I'm an idiot). So being the optimistic person  that I am, I just want to know if it is ACTUALLY gone or if there is still some hope.

I thought it might have been issues with the "grub" and so used the boot-repair thinga-magij to try and resolve the issue. I tapped that repair button a couple of times (probably 3).
Additional information: [http://paste.ubuntu.com/6564742/](http://paste.ubuntu.com/6564742/)


  So if all my Windows swag is lost, how can I get a brand new installation of Windows 8,  dual-booting with Ubuntu, with my original product key - no idea where I  can find it.


  I don't have any backup/recovery files either - the external's corrupted.


  

  Tutorial followed: [URL="http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html"]http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html
[/URL]

  Any kind of help would be highly appreciated.

---

### Post by hg-knight on 2013-12-13
Most computer have a "Recovery" partition which is used to re-install  Windows. Typical you press a specific "F" key (F8, F10, F11, Etc) when  you first boot the computer to start the recovery process.
  
 Check your PC manufacture's support web site, your owner's / user's guide or try contacting the support team for your PC.

---

### Post by celoitaliano on 2013-12-13
The same thing happened to me. I have a Dell Inspiron, came with win8 installed. I will try all the Fs, good luck to both of us.

EDIT: 
It worked. 
I have the CD of pirate Windows 8. I restarted my pc with the CD inside and pressed F12.
Than, BOOT SETTINGS -> LEGACY BOOT MODE -> Install Windows 8 
I had to delete UBUNTU partitions because the partition system was something like GTF and needed to be FAT something...
Than created the new partiton to install WINDOWS. I'll reinstall UBUNTU later(and try to not uninstall Windows again)

---

### Post by oldfred on 2013-12-13
You chose the erase entire drive and install Ubuntu. That also erases the recovery partition.

You can see if testdisk can see old partitions and possibly see some of the old files with names. Or use photorec or other Windows tools to scan drive for files.

If you had some files that you must get back, you can get some of them back with tools that scan drive looking for anything that seems to be a file. They take a long time especially on large drives and you have to have space on another drive for the recovery. If you want to try that you need to STOP using system as every bit of use is overwriting more old data. Ubuntu is not large, and it installs all over the drive, so the part of the drive that was Windows will only have some data overwritten.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

For NTFS with Windows
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - Getdataback often recommended
[http://www.runtime.org/data-recovery-products.htm](http://www.runtime.org/data-recovery-products.htm)

 You may be able to contact vendor and get a recovery DVD set for a nominal charge. That would not be a full Windows install. I would never download an unknown Windows as it is sure to have built in virus or other issues.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
But only your vendor copy will work the key in the system.

Or you purchase a brand new copy of Windows. Or just use Ubuntu. :)

You probably will have to erase Ubuntu to install Windows as it has very particular partition requirements for UEFI boot. With BIOS boot it need primary partitions but will not correctly convert a gpt drive to MBR and other fixes are required.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by jefersen on 2013-12-13
celoitaliano: Thanks for letting me know!
But one of my main concerns with a windows re-installation is I won't be able to use my original product key. Any idea on how to retrieve that?

---

### Post by oldfred on 2013-12-13
As I understand the key only works with the vendor's version of Windows and it is then automatic.

---

