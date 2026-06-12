---
title: "Having trouble setting up an Ubuntu/Windows 8 dual boot"
date: 2015-09-23
forum: Installation &amp; Upgrades
---

### Post by SiddharthaWolf on 2015-09-23
Hi all! First of all, I've already posted this in the Windows section of this forum but as I haven't yet got a response and this issue is quite urgent, was hoping that this forum - being busier - might be a better choice. Apologies if this is frowned upon. :(

For background info, the machine is an Asus F-551-M which came with  Windows 8 pre-installed (I then added Ubuntu later, which worked  reasonably happily for a short time before problems started - it didn't  bother me too much at the time though because I never used Windows).

I've had problems with Windows 8 dual-booting with Ubuntu for a while so  I tried starting again from scratch. I removed (using OS-Uninstaller)  my Windows partition and completely reinstalled. Everything was OK and I  was able to access Windows, but not Ubuntu (even by the long route you  should be able to when Windows hogs the boot). I then used the Boot  Repair tool within Ubuntu Live to fix this, which returned Grub and I  was momentarily pretty happy.

However, I now have similar problems to those I had previously and am  hoping there's something fairly simple I can do to sort it out.

Now when I get to the Grub menu, I have the following boot options (numbered for easy reference):

 1. Ubuntu  
 2. Advanced Options for Ubuntu 
 3. Windows UEFI bootmgfw.efi
 4. Windows Boot UEFI loader 
 5. EFI/Ubuntu/MokManager.efi 
 6. Windows Boot Manager (on dev/sda2) 
 7. System Setup

The Ubuntu boot works without a problem. I haven't tried 2 as it's presumably irrelevant to determining the problem.

 - 3 goes into "preparing automatic repair" then "Automatic Repair
   couldn't repair your PC" 
 - 4 leaves me with a black background and the blue window silhouette under which dots eternally circle 
 - 5 leads to "SHIM KEY MANAGEMENT" "Press any key to continue", after  which I get three options "Continue Boot", "Enroll key from disk" and  "Enroll
   hash from disk". 
 - 6 continues to "preparing automatic repair" then "Diagnosing your PC"  then "checking disk for errors - this might take over an hour" then  "AUTOMATIC REPAIR" then leaves me a message "Logfile:  C:\\Windows\System32\Logfiles\Srt\SrtTrail.txt" before giving me the  options "Shut Down" or "Advanced Options" (which include all the  standard options "Continue" (which goes back to grub), "Use a device",  "Troubleshoot" and "Turn off"). 
 - 7 Leads to my BIOS

I went in with GParted (within Ubuntu Live USB) again to check the partitions and they are as follows:

 - SDA1 Fat32    boot
 - SDA2 ext4  
 - unallocated
 - SDA4 unknown  msftres
 - SDA5 ntfs     msftdata
 - SDA6 linux-swap
 - unallocated
 - SDB1 fat43 /cdrom  boot/lba (the Ubuntu live USB presumably)

In addition, I noted the Boot Repair log when I made the adjustments just before the Windows boot problem:

[http://paste.ubuntu.com/12400329](http://paste.ubuntu.com/12400329)

Any help you could give would be much appreciated as I will need Windows for work soon. Thanks in advance.

---

### Post by oldfred on 2015-09-23
I do not see any issues.
But grub can only chain load to a working Windows. It does not work if Windows has issues.

It was able to find the Windows, so it does not seem you left it hibernated, or that it needs chkdsk, but best to double check.

Can you start Windows directly from UEFI boot tab or one time boot key often f10 or f12, check your manual? If errors see if you can get into f8, or Windows internal repair console.

Since grub only boots working Windows always best to have a Windows repair flash drive. And keep Ubuntu live installer as Ubuntu repair tool. Boot-Repair cannot fix most Windows issues.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

