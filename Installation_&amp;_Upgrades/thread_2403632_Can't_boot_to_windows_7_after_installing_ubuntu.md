---
title: "Can't boot to windows 7 after installing ubuntu"
date: 2018-10-14
forum: Installation &amp; Upgrades
---

### Post by bearnithi on 2018-10-14
Hello ubuntu masters, 

I am new to the ubuntu world, yesterday i had installed the ubuntu along with windows 7. For some reasons, "install ubuntu along side windows" option is not there. So i go to something else. Where i have unallocated space for ubuntu (i shrunk my windows space). 

There were 4 paritions. In order to install ubuntu, i have to create an another partition. Unfortunately, i deleted the system reserved partion of windows (which is 101 mb in size). 

After that, i created a new partition from un allocated space and installed ubuntu in it.

Ubuntu is working fine, i can even access the files in windows from ubuntu. But i cant boot to windows 7.

Is there any way to manually place the booting file in the deleted parition. I had even try to boot through usb, but ubuntu grub always comes. 

I have tried a whole day, now i realise that you masters can help me. Thank you.

---

### Post by ajgreeny on 2018-10-14
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system. 

I wonder where that unallocated space on your disk is; you say you shrunk the Windows space but give us no detail about where it now is in the system, however, you should have used Windows own disk management utility to shrink the Windows space, then allowed it to run chkdsk a couple of times to ensure it was still bootable. The Boot-Info output will give us a lot more detail.

---

### Post by bearnithi on 2018-10-14
Thank you for the answer @[COLOR=#000000]ajgreeny,

I have followed your instructions. here is the pastebin link

[/COLOR][http://paste.ubuntu.com/p/vVm93VYWCB/](http://paste.ubuntu.com/p/vVm93VYWCB/)

---

### Post by yancek on 2018-10-14
Posting the link you get from running boot repair should provide enough info for someone to make a suggestion.  Two possible scenarios are that the windows partition you deleted was actually the boot partition for windows 7 which would be a real problem to resolve.  You may also have done an EFI install of Ubuntu while having a Legacy install of windows.  Boot repair should show this.

---

### Post by oldfred on 2018-10-14
You need to move boot flag with gparted (or Windows) to sda2 and then run a full set of Windows repairs.
       Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe  

You are missing the first two, and those cannot be fixed from Linux or Linux tools.
You can use a Windows installer's repair mode or a Windows 7 repair flash drive's repair console.

      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Windows will put its boot loader into MBR. You then need to run Boot-Repair or manually restore grub to MBR.
run this to add Windows to grub menu.
sudo update-grub

---

### Post by mastablasta on 2018-10-15
> **bearnithi said:**
> 
There were 4 paritions. In order to install ubuntu, i have to create an another partition. Unfortunately, i deleted the system reserved partion of windows (which is 101 mb in size). 


also you deleted the boot partition. bad idea. you shouldn't delete anything. you just need to change (at least) one of windows primary partitions into a secondary one (extended). how to do that?

1. backup data first (clonezilla, redobackup...)
2. use minipartition wizzard to transform one partition (data?!) to secondary
3. create unformated disk space
4. continue with linux installation

---

### Post by bearnithi on 2018-10-15
Can I boot (windows) using USB to repair my windows? will it solve my issue?

---

### Post by oldfred on 2018-10-15
Windows repair flash drive should work, but you must move boot flag first as it only wants to repair primary NTFS partitions with boot flag.

---

### Post by bearnithi on 2018-10-15
Followed ur steps, iam able to boot to windows. But dual boot option is not showing. How can i bring back ubuntu too. Its still in a separate partition

---

### Post by oldfred on 2018-10-15
Windows repairs should have restore the Windows boot loader to MBR.
You then need to restore grub to MBR and update grub to add Windows to grub menu.
You can use Boot-Repair from live installer.

---

### Post by bearnithi on 2018-10-15
Is there any step by step guide to do it?. It would be pretty much helful for me..

---

### Post by oldfred on 2018-10-15
You may be able to just use the autofix that Boot-Repair wants. 
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
Only if major issues, is then the advanced option of total uninstall and reinstall of grub required.
It should run this as part of its updates, but if Windows not in grub menu, once you boot into Ubuntu run this:
sudo update-grub

---

### Post by bearnithi on 2018-10-16
Thanks a lot. Its working...

---

### Post by oldfred on 2018-10-16
Great.
You can change to Solved.

---

