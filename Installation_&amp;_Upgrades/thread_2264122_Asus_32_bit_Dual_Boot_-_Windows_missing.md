---
title: "Asus 32 bit Dual Boot - Windows missing"
date: 2015-02-05
forum: Installation &amp; Upgrades
---

### Post by james_king2 on 2015-02-05
I am totally new at even trying to do any Dual Boot system so, I will probably ask some not so bright questions. First I am using an older Asus 32-bit desktop with 2GB Ram. Now I have just installed a new Seagate 750 GB hard drive with a fresh installation of Windows 7 Pro. For the past several nights I have been letting Windows install 200+ updates to the system files. I made a System Restor back up disk with Just Windows 7 "only" installed and before any updates were added. I also made another disk after most of the updates had been installed. Then, I made a backup file of the complete system in a folder on a USB Drive. (Hopeing to avoid the usual Windows stuff!) Then, I ran Ubuntu 14.04.1 LTS from an ISO CD with the Install along side the Windows system. Ubuntu roughly split the drive in half concerning the partitions. 
When I run Ubuntu I don't see anything that would allow me to boot Windows at all. Does this mean I have to do a repair of some sort to get to Window from Ubuntu as well?

---

### Post by oldfred on 2015-02-05
Moved to your own thread as boot issues almost always are unique.

Have you run this from a terminal in your Ubuntu:
sudo update-grub

If that does not add Windows to grub menu, post link to Summary report.
Boot-Repair can only do minor repairs to Windows, you also have to have a disk to run Windows repairs.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Did you leave Windows hibernated?
Or did you not resize Windows using its own tools?
Some have issues letting the Ubuntu installer resize Windows. After Windows resize it must be immediately rebooted as it has to have chkdsk run to repair itself to its new size. And Grub only really boots working Windows.
You may have to restore Windows boot loader, boot using f8 to get into repairs, or use the Windows installer or a Windows repairCd/Flash to run Windows repairs.
Then after Windows works, restore the grub boot loader to the MBR which either Boot-Repair or manually.

---

### Post by james_king2 on 2015-02-06
Oldfred, first thank you. I actually saw the window pop up on about the thrid re-boot that listed Windows 7. The menu was very, very small but I caught it and arrowed down to the W 7 listed and clicked on it and Windows started loading after it had gone through Chkdisk. Everthing seems to be up and running okay. Thank you again, Jim

---

### Post by oldfred on 2015-02-06
Small menu may be related to font size and/or default screen resolution that grub picks up.

You may be able to adjust that if desired, but may have to copy font to grub folder. 
And you should make a Windows repair flash drive and have a good full backup of Windows as that is not easy to reinstall like Ubuntu can be. But even with Ubuntu your data and configuration needs to be backed up.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)


 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

