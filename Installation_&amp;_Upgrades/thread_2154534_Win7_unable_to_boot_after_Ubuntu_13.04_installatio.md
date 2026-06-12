---
title: "Win7 unable to boot after Ubuntu 13.04 installation"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by userjjb on 2013-06-15
First the problem: After a new 13.04 install, on startup I am greeted with GRUB; I can properly boot into Ubuntu, but if I choose Win7 from GRUB it says Windows did not start properly. If I choose "Start Normally" it briefly flashes the Win7 startup logo and then immediately changes to a screen that says "Windows is loading files" with a load bar (low-fi ASCII style) that completes two cycles and the dumps me back to the initial GRUB screen. If I choose "repair startup" it does the same thing only it pushes me back to the screen to choose how to start Windows (normally/repair startup). I would like to be able to be able to boot Windows successfully obviously.

I have a i7 processor with 1 SSD and 2 HDs. Windows 7 is installed on the SSD and was done in UEFI mode.

In preparation for my first install of Ubuntu I shrank the NTFS volume on the SSD and one of the HDs from within Windows using the "Disk Management" tool to allow unpartitioned space for / and swap. I made to sure to restart and boot back into Windows afterwards to allow it to repair/shift data as necessary. I created a bootable USB drive with the 13.04 ISO and booted in UEFI mode and installed Ubuntu, with / on the SSD and swap on the HD (leaving some additional unpartitioned space on the HD for future use).

After install I was greeted with a prompt saying WIndows didn't boot properly last time, with an option to repair startup or boot normally, neither of which properly booted Windows. After looking in my BIOS I realized I never turned off Fast Boot (which I understand can sometimes cause issues), I turned it off but nothing changed.

I next booted up the Live version of Ubuntu from USB and ran Boot Repair, my paste is [http://paste.ubuntu.com/5766693/](http://paste.ubuntu.com/5766693/)

After the Boot Repair I was instead greeted with GRUB and am able to boot into Ubuntu, but unable to boot into Windows with either Grub option for Windows (one says "Windows Boot UEFI Loader", the other says "Windows UEFI bkpbootmgfw.efi") both give the above descibed problem behavior.

Suggestions/solutions?

---

### Post by Mark Phelps on 2013-06-15
Did you  mistakenly use the option in the Ubuntu installer to shrink Windows using the SLIDER?  IF so, that most likely corrupted the Windows filesystem, as it has done that on occasion.  

It generally takes Startup Repair at least three passes to completely fix any boot problems.  So, if you've not run it that many times, try it again a couple of times.

---

### Post by oldfred on 2013-06-15
If you have Windows 7, you will not have secure boot issues.

But Boot-Repair runs a Windows file rename on second run because many Windows 8 systems will only boot the Windows efi file with secure boot on. You then have to rename shim to be the Windows file, but then can only boot Windows from grub menu as the Windows efi file is renamed.
You can undo the file rename and should then be able to directly boot Windows (or ubuntu) from UEFI and run the Windows repairs.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply


 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

You also have a backup.

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by userjjb on 2013-06-17
*@Mark *Phelps Didn't mess with Win partition at all. I also allowed windows many attempts to correct itself, with no result. I even went so far as to try and use the repair utility on my Win7 install disk.

*@oldfred* I appreciate all the advice. I experimented with SecureBoot, restoring backups, renaming, and several other possibilities.

After 1.5 days of troubleshooting I decided to just backup any wanted data off the Win7 partition and re-installed Windows thinking I must have messed up somewhere. With a fresh Win7 install I re-installed Ubuntu and had the same exact same issues.

**Resolution:**
I decided that Windows didn't like sharing the ESP on sda (my SSD) with Ubuntu so I made a second ESP on sdb (my HD).
-I installed Ubuntu first. I put / and /home on sda and swap on sdb, selecting sdb1 (the ESP) as "Device for bootloader installation".
-Next I installed Win7 on sda. I found that the installer secretly was selecting the ESP on sdb and so wasn't creating one for itself on sda. I unplugged sdb and restarted the install and Win7 now properly created a ESP for itself on sda.
-Windows booted without issue, but Ubuntu wouldn't boot properly so I ran Boot Repair's recommended option to fix it.

I am now able to properly boot both OSes, both of which primarily reside on my SSD. I hope this may prove useful to others who are having trouble getting Win7 and Ubuntu to play nice on the same ESP.

---

