---
title: "Need Help Installing Ubuntu on a Windows 7 Machine"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by crazy_lazy_bear on 2009-11-29
Hello All,

     I have researched my issue with no success.  I have read [this article]("http://apcmag.com/print.aspx?id=1279&mode=print"): [http://apcmag.com/print.aspx?id=1279&mode=print](http://apcmag.com/print.aspx?id=1279&mode=print).  
     Background info: I bought a brand new Sony Vaio from a box store with Windows 7 preloaded.  A Windows install disc was not included.  I notice that Windows 7 uses a 100Mb boot partition that is separate from the Windows partition.  I successfully installed Ubuntu 9.10 from the live CD onto a ext3 partition (that I named "Ubuntu").  I chose to install GRUB in the Ubuntu partition.  In the past, on XP machines, I would copy ubuntu.bin to the C: drive and add "C:\UBUNTU.BIN="Ubuntu"" as the last line to the Windows bootloader.  In Windows 7, I do not know how to edit the Windows bootloader. I downloaded and installed EasyBCD.  My goal was to copy the boot entries from menu.lst to the NeoGrub menu.lst file.

     My first issue is that there is no menu.lst file in /boot/grub.  I do not know why it isn't there.  Because the machine does not give me an option to boot Ubuntu at startup, I am using the live CD and using the command "sudo gedit /media/Ubuntu/boot/grub/menu.lst".  The menu.lst file comes up empty.  

     My second thought was to install GRUB on the Windows side.  However, I'm not sure if it belongs in the 100Mb boot partition or the regular Windows partition.

     Any help you can provide is appreciated.  Thank you.

---

### Post by darkod on 2009-11-29
First of all, 9.10 comes with grub2 which does not use menu.lst that is why it's opening as empty (new) file.
Second, unless you really have a valid very important reason to keep windows bootloader, you're just making your life complicated for yourself trying to add ubuntu to windows bootloader which is desgined to ignore everything except windows.

Just reinstall grub2 on the MBR and you should be OK. Don't know if you installing grub2 on the partition of ubuntu might confuse it, never done that before.

Grub2 will not be written on the 100MB partition, it will be on the MBR, Master Boot Record, that's actually part of the HDD you don't usually see.

Good and short instructions how to reinstall grub2:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by phillw on 2009-11-29
> **crazy_lazy_bear said:**
> Hello All,

     I have researched my issue with no success.  I have read [this article]("http://apcmag.com/print.aspx?id=1279&mode=print"): [http://apcmag.com/print.aspx?id=1279&mode=print](http://apcmag.com/print.aspx?id=1279&mode=print).  
     Background info: I bought a brand new Sony Vaio from a box store with Windows 7 preloaded.  A Windows install disc was not included.  I notice that Windows 7 uses a 100Mb boot partition that is separate from the Windows partition.  I successfully installed Ubuntu 9.10 from the live CD onto a ext3 partition (that I named "Ubuntu").  I chose to install GRUB in the Ubuntu partition.  In the past, on XP machines, I would copy ubuntu.bin to the C: drive and add "C:\UBUNTU.BIN="Ubuntu"" as the last line to the Windows bootloader.  In Windows 7, I do not know how to edit the Windows bootloader. I downloaded and installed EasyBCD.  My goal was to copy the boot entries from menu.lst to the NeoGrub menu.lst file.

     My first issue is that there is no menu.lst file in /boot/grub.  I do not know why it isn't there.  Because the machine does not give me an option to boot Ubuntu at startup, I am using the live CD and using the command "sudo gedit /media/Ubuntu/boot/grub/menu.lst".  The menu.lst file comes up empty.  

     My second thought was to install GRUB on the Windows side.  However, I'm not sure if it belongs in the 100Mb boot partition or the regular Windows partition.

     Any help you can provide is appreciated.  Thank you.

9.10 uses Grub2 - the Howto for dual booting Win and 9.10 is over here -->  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  That'll tell you how.

You should, however, be able to issue ```
 sudo update-grub 
``` from the ubuntu area and it *should* find your Win area for you.

Regards,

Phill.

---

### Post by sailor2001 on 2009-11-29
gksudo gedit /boot/grub/grub.cfg

---

### Post by crazy_lazy_bear on 2009-11-29
Thank you for your help.  The links you sent worked perfectly.  Thank you.

---

### Post by audiomick on 2009-11-29
please put a "solved" tag on the thread.
it is available in the thread tools drop down at the top of the thread

---

