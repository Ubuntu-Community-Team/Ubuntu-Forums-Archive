---
title: "Can't boot into Windows 7 in multiboot os"
date: 2015-07-06
forum: Installation &amp; Upgrades
---

### Post by votuongtho on 2015-07-06
[TABLE]
[TR]
[TD="class: postcell"]         
[/TD]
[/TR]
[/TABLE]
I installed Ubuntu 14.04, Windows 7 and Windows 8.1 in the same  computer. Whenever I boot my computer, there is the boot options (1):
  
[LIST]
[*]Ubuntu
[*]Ubuntu configuration
[*]Ubuntu memtest
[*]Windows 8
[/LIST]
  When I choose Windows 8, it will reboot to Windows boot options (2):
  
[LIST]
[*]Windows 7
[*]Windows 8.1
[/LIST]
  If I choose Windows 7, it will boot directly to Windows 7 and  vice  versa. But after a few crash recently, I can't boot into Windows  option,  whenever I chose the Windows 8 options in (1), it would reboot  back to  (1), it didn't open the Windows option like (2). I tried to use  a  bootable usb to restore the Windows to early system restore but  after  restarted, the problem still didn't solve.
  I used Boot Repair in Ubuntu to fix but it didn't work either. Here is the [log]("http://pastebin.com/raw.php?i=AuJ29hWt")

I am quite new with Ubuntu so I really appreciate any help.

---

### Post by oldfred on 2015-07-06
Boot-Repair is primarily for Linux boot issues. It can only make minor repairs to Windows.
Grub only boots working Windows.

So you need a current version Windows repair flash drive for every version of Windows you have installed. And as I do in Linux I also have several other repair tools as live bootable systems.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

            Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

    
Have you installed everything in BIOS or UEFI boot mode.
Windows often needs chkdsk, which you can only run from Windows. Or BCD repairs, since your BCD has both Windows entries.
Since Windows issues, you may want to restore Windows as default boot. You can do that restore with Boot-Repair or your Windows repair or install flash drive or DVD. 

Then once Windows is fixed use Boot-Repair to restore grub2's boot loader.

If UEFI, you directly boot from UEFI boot menu.

---

### Post by votuongtho on 2015-07-06
Thank a lot for your answer! I will try to select boot from Windows as default options. I already made a Windows 7 repair with my usb drive, should I need another 1 for Windows 8?
> 
Have you installed everything in BIOS or UEFI boot mode.

I am not sure but I thought it may be BIOS mode
> Windows often needs chkdsk, which you can only run from Windows. Or BCD repairs, since your BCD has both Windows entries. I don't know what BCD stand for, please explain!
> Since Windows issues, you may want to restore Windows as default boot.  You can do that restore with Boot-Repair or your Windows repair or  install flash drive or DVD. 


Already set, I will reboot right now!

---

### Post by oldfred on 2015-07-06
Windows BCD - Boot Configuration Data 
That replaced XP's boot.ini which was plain text. The BCD is some sort of hive and requires Windows tools to edit.
      
 BCDboot Command-Line Options Windows Vista/7/8 recreates boot files.
[http://technet.microsoft.com/en-GB/library/hh824874.aspx](http://technet.microsoft.com/en-GB/library/hh824874.aspx)


 [http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

I had a Windows 7 repairCD/flash that I used on my XP for running chkdsk.So I would think you may be able to use Windows 7, but do not really know. Often better to have newer version as repair tool, as it may have updates and do a better job.

---

