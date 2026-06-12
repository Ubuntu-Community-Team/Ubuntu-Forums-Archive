---
title: "Uninstallation of ubuntu bootloaderd with windows 8.1 dual boot"
date: 2014-03-05
forum: Installation &amp; Upgrades
---

### Post by drew13 on 2014-03-05
Hello, I'm relatively new to Ubuntu in general and was wondering how I would go about uninstalling ubuntu 13.10. I got a new computer and would rather use unbuntu on that instead of this one. I have deleted the hard drive partions, however I apppear to be unable to figure out how to override the Ubuntu bootloader with windows. As I previously stated, I'm relatively new to Ubuntu and am quite scared as to what might happen if my computer were to shut down without uninstalling the bootloader first. I did some research and still couldn't figure out how to delete the bootloader, as most tutorials were created for Windows 8, not 8.1. What I understood was this: create a windows live DVD, boot with that, click on repair system, and fix it from there. However I am quite confused on how to create a system repair disc on windows 8.1. I sincerely apologize if this was posted in the wrong place, as I could not find an ubuntu UN-installation sub forum, this is as close as I got to that. Any help would be greatly appreciated!

UPDATE: Ok so I tried booting from a CD using boot repair as suggested. I burned the .ISO to a DVD-R, and went to change PC settings>Update and Recovery>Recovery>Advanced startup (because Windows 8.1 doesn't really fully shut down enough for you to access the BIOS settings). However it took to to the Ubuntu GNU GRUB and I had to type exit into the GRUB command line, it then continued to boot windows 8.1, and did not boot from the CD like I had tried to do. While I can breathe a sigh of relief because I can still boot into windows through the Linux GRUB even with Linux uninstalled, I don't want to have to go through the command line every time I restart my computer. Maybe there is a way I can access this computers files from another computer?

---

### Post by phidia on 2014-03-05
Maybe you can use [boot repair]("https://help.ubuntu.com/community/Boot-Repair") to fix the MBR (master boot record).
Take a look at the link I've inserted.

---

### Post by Mark Phelps on 2014-03-05
> create a system repair disc on windows 8.

For future reference, a really good Windows 8 forum is eightforums.com -- you should bookmark that and go there for Win 8.1 advice.

As to creating a system repair disk, use the following tutorial (from eightforums): [https://www.google.com/url?q=http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html&sa=U&ei=zvkXU530Aon40wHVioCICw&ved=0CBAQFjAF&client=internal-uds-cse&usg=AFQjCNEiAi9BpOeGfeZ3td75STKVvelEUA]("https://www.google.com/url?q=http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html&sa=U&ei=zvkXU530Aon40wHVioCICw&ved=0CBAQFjAF&client=internal-uds-cse&usg=AFQjCNEiAi9BpOeGfeZ3td75STKVvelEUA")

---

### Post by ubfan1 on 2014-03-06
A UEFI machine can have  multiple bootloaders, and unless you have run boot-repair and "renamed" the bootloaders, the ubuntu bootloader is just sitting in a directory (/EFI/ubuntu).  If you had run the boot-repair rename function, then copied of the Ubuntu bootloaders are sitting in the windows bootloader location too, named what the windows bootloaders were named, and they were renamed to bkpbootmgfw.efi or something like that.  If you had done that, select the unrename function to clean things up.  Check that the "backup" bootloader in /EFI/Boot/bootx64.efi is really a  copy of the Windows bootloader (look at the size).  Normally that one will not run, but under some failure conditions, it might be invoked.  Now set the default bootloader to be a windows bootloader (use efibootmgr on the Ubuntu side.  You should be able to select the Windows bootloader from the efi boot menu (usually some function key at boot, varies by machine) to invoke Windows even before cleaning everything up, as long as the names the nvram points to are the bootloader you want (and not the renamed ones from a possible boot-repair).

---

### Post by drew13 on 2014-03-06
So I just reboot my computer from the live CD even though the Linux bootloader (before I uninstalled it) comes up before the windows one does? If I tried to restart my computer right now would I be able to go back to windows or would my system crash?

---

### Post by oldfred on 2014-03-08
You should always be able to boot Windows directly from UEFI, unless you ran the 'buggy' UEFI fix as mentioned above.

You have to remove Ubuntu folder in efi partition or UEFI will readd it to UEFI NVRAM.

 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

      
 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by drew13 on 2014-03-10
> **oldfred said:**
> You should always be able to boot Windows directly from UEFI, unless you ran the 'buggy' UEFI fix as mentioned above.

You have to remove Ubuntu folder in efi partition or UEFI will readd it to UEFI NVRAM.

 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

      
 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

I don't understand what live CD you're talking about. If I could boot from a live CD then I wouldn't have this problem, and wouldn't have to do ^^that^^. Is there a way to boot from a CD using the terminal on the GRUB? If so, then I could run a system repair disc and easily fix the problem, however I appear to be struggling with booting from a Live CD.

---

### Post by oldfred on 2014-03-11
Are you gettting grub menu and then having video issues, so it seems like it is not booting.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
What video chip?
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by drew13 on 2014-03-19
> **oldfred said:**
> Are you gettting grub menu and then having video issues, so it seems like it is not booting.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
What video chip?
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)


Yes I could do that. Perhaps there is a way to access the bootloader files using the file explorer and delete the Linux GRUB from there? I have an Nvidia Geforce GTX 765m (yes it's a card for a laptop. Hence the 5 after the 76)

---

