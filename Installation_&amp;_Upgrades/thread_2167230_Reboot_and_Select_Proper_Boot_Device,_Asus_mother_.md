---
title: "Reboot and Select Proper Boot Device, Asus mother board"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by bob17 on 2013-08-12
My Asus homebrew was setup with windows 7 in a removable hard drive and worked perfectly for over 3 years . I pulled out the windows 7 hard drive and inserted a new drive and installed ubuntu 12.04.2-amd64 and It worked perfectly. Later, I removed the ubuntu drive and returned the windows 7 drive. Windows 7 would no longer boot with message "Reboot and Select Proper Boot Device" I made sure the bios had selected the hard drive as the boot device, I made sure the drive was connected by removing and reinstalling, I turned off the power and pulled the power cord. Still failure. In desporation I reinserted the ubuntu disk drive which booted ubuntu perfectly. Then reinserted windows 7 disk drive, expecting failure, and wala it booted as if nothing was ever wrong. So I guess this one is [SOLVED] sortof. 
On the internet I read many suggestions as drastic as resetting the bios, booting in safe mode (it recognized only the CDROM as the boot device), press F9 for Asus boot tool, using grub, reinstalling windows, reseating the hard drive etc but the above trial and error method worked without all but one of these suggestions. I inserted the hard drive several times with firmness, I hurd the drive spin up, I know data and power (SIDE) are on seperate connectors which could account for the spin up but no data.

---

### Post by oldfred on 2013-08-13
You always need to know what boot loader is installed in the MBR and then what it needs to boot from. Ubuntu's grub may be in one MBR but need boot files from another drive.
Windows can even be installed in one drive and have its boot partition on another drive.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by bob17 on 2013-08-19
[LIST]	I had not considered the boot	sequence. In this case, there is only one disk drive in the system,	a removable SIDE drive installation. The Ubuntu drive had an	existing XP(32) OS which during Ubuntu installation was completely	removed. At least that is what the Ubuntu installer said.

To help understand if this is a	hardware or software problem, I reinserted the Windows 7 drive, and	this time it booted perfectly on the first try. In conclusion, I	think I had a hardware connector problem.
[/LIST]

---

