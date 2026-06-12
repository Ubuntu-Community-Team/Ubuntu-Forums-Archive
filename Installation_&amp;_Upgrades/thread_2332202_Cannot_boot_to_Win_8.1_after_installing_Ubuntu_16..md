---
title: "Cannot boot to Win 8.1 after installing Ubuntu 16.04.1"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by A4Skyhawk on 2016-07-29
Here is my boot-repair report.  I have not executed any boot-repairs yet, though:
[http://paste2.org/EOZ3fsV4](http://paste2.org/EOZ3fsV4)

      Before installing Ubuntu 16.04.1, my PC (Acer Aspire XC-603/Aspire XC-603) was set up with a dual boot of Win 8.1 (pre-installed) and Ubuntu 16.04.  The dual boot UEFI worked fine as I was able to select either Ubuntu or Win 8.1.  After installing Ubuntu 16.04.1, I cannot boot to Win 8.1.  The Grub menu is the same as before, but when I select “Windows Boot Manager”, I get the following display:

[IMG]http://i246.photobucket.com/albums/gg88/Skyhawk624/Misc/P1010048.jpg[/IMG]

During the install I set the “Device for boot loader installation” to /dev/sda ATA……...”.

I have a usb memory stick with the Win 8.1 recovery files, but when I  insert the stick and reboot, the computer does not recognize it (even  though I have Removable Device as #1 boot priority) and goes right to  the Grub menu.  Strangely, after booting into Ubuntu 16.04.1, and  launching Files, and then inserting the usb Win 8.1 recovery stick,  Files will recognize the usb for a very short time, then not show  anything in the usb port.  However, if I insert the usb Win 8.1 recovery  stick for another computer (Lenova), Files will detect it and show it.   I don’t know why there is a difference as both sticks were OK before.  
  
In   Ubuntu Files I can open the Win 8.1 OS and all the folders  and files appear.  I did find the file “BCD”, shown in the above pic.,  at Win\Boot\DVD\EFI\BCD.  

Any suggestions for what step(s) should be taken next will be appreciated.  
TIA,
A4Skyhawk

---

### Post by oldfred on 2016-07-29
Most often issue on grub not booting Windows is that is it hibernated or needs chkdsk. Both of those prevent grub from chain loading to Windows & have Windows work.
Grub really only boots working Windows.

Can you in UEFI or one time key like f10 or f12 choose from UEFI boot to directly boot Windows? You may need f8 to get into its internal repair console.

If you installed Ubuntu I would expect you to be able to use USB flash drive. But if you update UEFI from Acer that resets everything to defaults and you may have to make sure in UEFI that allow boot or allow use of USB ports or boot from USB ports is enabled.

---

### Post by A4Skyhawk on 2016-07-29
On bootup, I can get to UEFI menu w/ F12.  But selecting Windows returns a window shown in my pic above.

---

### Post by oldfred on 2016-07-29
Can you press f8 immediately after the f12? That may get you into the internal Windows repair console. If not then as it suggests you need a Windows repair disk.

If you have access to another Windows 8.1 system, work, school, friend, you can make a repair disk.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[URL="http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/"]http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/

[/URL]
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive) 

Is today last day for "free" upgrade to Windows 10?

[URL="http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/"]
[/URL]

---

### Post by A4Skyhawk on 2016-07-29
F12 then F8 did not work.
Here are pics of running "Disc" on the 2 Win8.1 usb recovery sticks that I made when setting up the PCs.
For my Acer, on which I installed 16.04.1, but will not boot to Win:

[[IMG]http://i246.photobucket.com/albums/gg88/Skyhawk624/Misc/Win8.1Recovyfor%20Acer.png[/IMG]]("http://i246.photobucket.com/albums/gg88/Skyhawk624/Misc/Win8.1Recovyfor%20Acer.png")

For my Lenova, which has 16.04 and Win 8.1:

[[img]http://i246.photobucket.com/albums/gg88/Skyhawk624/Misc/Win8.1RecovyforLenova.png[/img]]("http://i246.photobucket.com/albums/gg88/Skyhawk624/Misc/Win8.1RecovyforLenova.png")

I see that the one for my Acer is "bootable".  But when I boot up, the pc does not go to the usb.  (Strange that this usb stick was detected by "Disc", but not by "Files" on either pc.)
I also see that both are FAT 32-bit.  Both of my PCs are 64-bit.  Does that mean they're not usable?

---

### Post by oldfred on 2016-07-29
The FAT32 has no relation to a 64 bit system. Other than size of files you can save is limited with FAT32 to 4GB. 

If partition has corruption then chkdsk from Windows or dosfsck may be required. But it could that that they are just images for recovery and would not show normally in Ubuntu anyway.

Can you plug in flash drive with recovery and boot Ubuntu either install or live installer.
Then run Boot-Repair's summary report. It may tell us if MBR of flash drive is ok. And if PBR of flash drive is ok. Beyond that then it is just Windows and Linux cannot do much.

---

### Post by A4Skyhawk on 2016-07-29
Boot-repair summary for Acer (16.04.1 + Win 8.1): [http://paste2.org/Av22Vn1h](http://paste2.org/Av22Vn1h)

Boot-repair summary for Lenova (16.04 + Win 8.1):  [http//paste2.org/xEkjb4Fv]("http://paste2.org/xEkjb4Fv")

---

### Post by oldfred on 2016-07-29
You first link shows sdc1 with typical flash drive UEFI boot files (but not BIOS)
 Boot files: /efi/boot/bootx64.efi /bootmgr /boot/bcd 

You second one shows no boot files at all, neither BIOS nor UEFI.

 No boot loader is installed in the MBR of /dev/sdc.

---

### Post by A4Skyhawk on 2016-07-29
Is either recovery stick usable, or fixable so that it can be used?

---

### Post by oldfred on 2016-07-29
The one should boot in UEFI mode (only). The other is not bootable, may be just data?

So in UEFI choose to have USB boot in UEFI mode and USB should show as a boot option.

---

### Post by A4Skyhawk on 2016-07-30
I was able to use Disk and edit the "mount options" to "mount at startup".  Then reboot, tap F12 to get to the device menu, and select the usb recovery stick for startup.  This got me to the Win Troubleshooting screen.  I selected "command prompt" and typed in "echo list volume | diskpart", which displayed a table of data on the "volumes" and assigned "letters" and sizes for the partitions on the harddrive.  The labels and sizes for each of the partitions shown in the data table matched what I get from gparted.  All but one of the "volumes" had an assigned letter, with which I performed "chkdsk X: /F /X".  They all checked out OK.  I could not run chkdsk on the one that does not have a letter assigned to it; this one is shown to have Fs of RAW, as opposed to NTFS or FAT32 for the others.  Based on its size, it corresponds to the "EFI system partition" in gparted, which indicates a mount point of /boot/efi; it also corresponds to sda2 in the boot-repair summary.
     From what I have gleaned from searching, I need to do the following, but want to confirm that these steps are correct and complete:
 1) Copy all files in sda2 and safe them in another location for retrieval later.
 2) Re-format this partition and make it FAT32, and assign a letter and label (ESP in gparted) to it.  
 3) Do a chkdsk on this partition.
 4) If chkdsk is OK, copy its files back into the partition.
 Do I have this correct so far?

 TIA

---

### Post by oldfred on 2016-07-30
Best to try either chkdsk or dosfsck before deleting partition.
Only if either of those does not solve issues, then deletion & recreating may be required.

Either way backup is always a good idea.

That I believe is the way to do it from Windows.

For FAT32 you can from Ubuntu run dosfsck. 
       Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by A4Skyhawk on 2016-08-03
[SIZE=2][FONT=arial][SIZE=3]Problem solved.  Here are the steps that I followed: [/SIZE]
                     [/FONT][/SIZE][SIZE=2][FONT=arial]Used “Disk” to set the usb sticks to “mount”.[/FONT][/SIZE]

[SIZE=2][FONT=arial]Used Ub LiveCD to run “Boot-Repair” summary report with each stick in the port and found that the stick for my pc was bootable, but not the one for the Lenova pc. [/FONT][/SIZE]

[SIZE=2][FONT=arial]Inserted bootable stick, booted pc, tapping F12 after the beep, and got the boot device menu.  I selected the bootable recovery stick, which brought up the blue Win screen to select language.  I then selected the “Troubleshoot” icon, then “Advanced opts”, then “Command prompt”.[/FONT][/SIZE]

[SIZE=2][FONT=arial]At the prompt I entered “echo list volume | diskpart”.  This displayed a table of data for 8 “volumes/partitions"; the labels and sizes for Win partitions matched the partitions shown in Gparted.  But the Fs for the 300MB (=sda2, efi) partition read RAW instead of FAT32.  This had to be reformatted.  So files shown in the Boot-Repair summary for sda2 first had to be saved.  I used Live CD and “Files” (sda2 mounted) to save to my usb b/u files memory stick.[/FONT][/SIZE]

[SIZE=2][FONT=arial]Then I used Win recovery stick again to get to Command prompt and entered, sequentially: diskpart, list disk, select disk # (for sda=0), list volume, select volume # (for sda2), format quick fs=fat32 label=ESP, assign letter=J, exit.[/FONT][/SIZE]
[SIZE=2][FONT=arial]Then entered “chkdsk sda2: /F /X”.  Result was OK, as it was for the other partitions.[/FONT][/SIZE]

[SIZE=2][FONT=arial]Then did  “echo list volume | diskpart” again.  Sda2 now showed Fs=FAT32, Label=ESP, letter=J.[/FONT][/SIZE]
[SIZE=2][FONT=arial]Then – back to Live CD - created the folders in sda2 to match what was on the Boot-Repair report:  “sudo mkdir /mnt/EFI” (etc, one step at a time.)[/FONT][/SIZE]
[SIZE=2][FONT=arial]Then inserted my usb b/u stick, made sure sda2 was mounted, and used 2 “Files” windows to “copy to” the files from the b/u to the proper sda2 folders.  [/FONT][/SIZE]

[SIZE=2][FONT=arial]Then inserted Win recovery stick, bootup (tapping F12) --> Troubleshoot window --> Advanced options --> then “Startup Repair”.   [/FONT][/SIZE]

[SIZE=2][FONT=arial]Removed recovery stick and re-booted.  It went to Win 8.1.  I checked the Win Disk Mngmnt, and it did not show any Ubuntu partitions.  This was reported on an Ub website as a bug.  Later, Gparted showed no changes to the partitions.  Also, none of my personal files in either OS were lost.   [/FONT][/SIZE]
[SIZE=2][FONT=arial]Booted to pc BIOS and changed boot order to Ub=#1, Win Boot Mgr=#2.[/FONT][/SIZE]
[SIZE=2][FONT=arial]Re-booted but the pc did not go to the Ubuntu OS.  Instead it displayed the following message:  [/FONT][/SIZE]
[SIZE=2][FONT=arial]“Welcome to emergency model.  After logging in, type “journalctl -xb” to view system logs, “systemctl reboot” to reboot, “systemctl default” or ^D to try again to boot into default mode.  Press enter for Maintenance or Cntrl+D to continue”.  Below the message was a grub> prompt. Pressed Enter and got same message.  Pressed Cntrl+D and got same message.[/FONT][/SIZE]
[SIZE=2][FONT=arial]Shutdown and used Live CD to run Boot-Repair “recommended”.[/FONT][/SIZE]
[SIZE=2][FONT=arial]Re-booted and got the grub menu – with many more options than before (&#8594; indicates where each lead):[/FONT][/SIZE]

[SIZE=2][FONT=arial]    Ubuntu &#8594; Ubuntu 16.04.1 on hard drive[/FONT][/SIZE]
[SIZE=2][FONT=arial]    Advanced options &#8594; recovery options window[/FONT][/SIZE]
[SIZE=2][FONT=arial]    Win UEFI bkpbootmgfw.efi &#8594; Win 8.1[/FONT][/SIZE]
[SIZE=2][FONT=arial]    Win Boot UEFI loader &#8594; Win 8.1[/FONT][/SIZE]
[SIZE=2][FONT=arial]    EFI/ubuntu/fwupx64.efi &#8594; recycles to this list[/FONT][/SIZE]
[SIZE=2][FONT=arial]    EFI//ubuntu/mokmanager.efi &#8594; a blue screen with a menu that recycled to this list and (?)[/FONT][/SIZE]
[SIZE=2][FONT=arial]    EFI/OEM/Boot/bootmgfw.efi &#8594; Win 8.1[/FONT][/SIZE]
[SIZE=2][FONT=arial]    Win Boot Mgr (on /dev/sda2) &#8594; recycles to this list[/FONT][/SIZE]
[SIZE=2][FONT=arial]    System setup &#8594; BIOS menu[/FONT][/SIZE][SIZE=3][FONT=Arial][SIZE=2][FONT=arial].
[SIZE=3]Problem solved.[/SIZE]
[/FONT][/SIZE]
[/FONT][/SIZE]

---

