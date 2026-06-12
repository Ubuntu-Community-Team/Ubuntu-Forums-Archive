---
title: "boot-repair not work to get back windows 7"
date: 2013-07-13
forum: Installation &amp; Upgrades
---

### Post by pqsbbs on 2013-07-13
dear, I installed ubuntu 13.04 in a machine which already has windows 7 installed. After installation completed, I checked files in windows 7 system partition exist, however, there is no start entry in grub list when pc boots.
Then I got boot-repair, and did both auto repair and advanced repair. It did not work.  There are only Ubuntu and test memory entries in grub list.
help! Thanks a lot in advance!

Here is bootinfo right after a fix:
[http://paste.ubuntu.com/5871593/](http://paste.ubuntu.com/5871593/)

Here is bootinfo after restarting pc:
[http://paste.ubuntu.com/5871620/](http://paste.ubuntu.com/5871620/)

---

### Post by papibe on 2013-07-13
Hi pqsbbs.

Did you use Boot-Repair from the Live CD, right?

Have you tried to solve it from Ubuntu itself using some of the grub utilities?

For instance, this should probe the OS currently available to grub:
```
sudo os-prober
```
To update that information on the grub menu, you should run this:
```
sudo update-grub
```
If it works correctly you should see Windows7 on the output of the command. You can also double check by probing again.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by fantab on 2013-07-14
> 
Windows not detected by os-prober on sda5. &#35760;&#24405;&#20102;1+0 &#30340;&#35835;&#20837; &#35760;&#24405;&#20102;1+0 &#30340;&#20889;&#20986; 32256&#23383;&#33410;(32 kB)&#24050;&#22797;&#21046;&#65292;0.000739223 &#31186;&#65292;43.6 MB/&#31186; **Warning: extended partition does not start at a cylinder boundary**. DOS and Linux will interpret the contents differently.

This error can be fixed with [FIXPARTS]("http://www.rodsbooks.com/fixparts/").
After fixing the error run '*sudo update-grub*' in ubuntu.

You may have to REPAIR Windows as I suspect that when you deleted the first partition and used the space for linux, you may have corrupted windows boot files. [Windows MBR Repair]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html") should be able to fix it.
I case you do windows repair and confirm that Windows is booting then you may find that Ubuntu is not booting. This normal as the Windows fix will corrupt Grub files on MBR. You can use Boot-Repair to fix it.

---

### Post by oldfred on 2013-07-14
Windows only boots from primary partitions formatted NTFS with the boot flag (active partition). Your install of Windows 7 is in sda5 which is a logical partition, so Windows will not boot from that partition.

Did you have another install of Windows in sda1 that you overwrote with Ubuntu? That partition was the boot partition and had the Windows 7 boot files which now are missing. 

Generally better to have Windows in primary partition(s) and let any Linux installs be in the logical partitions as Linux does not care and works equally well from primary or logical.

You are missing the two Windows 7 boot files.
 Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition) or in any other previous install with boot flag.
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You may be able to move boot flag from sda1 to sda2 since it is a primary NTFS partition and then from a Windows repairCD or flash drive repair your install. Otherwise you would have to either re-install Windows to a primary partition or convert the sda5 to a primary which you just about cannot do based on number of partitions and locations on drives. (all logical have to be inside one extended).

      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

