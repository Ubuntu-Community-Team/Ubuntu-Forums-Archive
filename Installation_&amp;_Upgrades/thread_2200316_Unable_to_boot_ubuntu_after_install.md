---
title: "Unable to boot ubuntu after install"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by Perezvon11 on 2014-01-18
Hello, 
I hope I am posting this to the right place. 

I recently mounted the 13.10 ubuntu iso to a flash drive on a windows 8, using the pendrive app.
I restarted my computer and loaded in the usb, I had no problem installing, it was all good, and then when I restarted it, the screen showed the vaio care, saying that there was nothing to boot to.

I then ran through the boot repair on the live usb. The repair said it was successful, and still when i restart I get the same thing- Vaio care, nothing to boot.

paste.ubuntu.com/6775788 is my boot repair link.

maybe some problem with the uefi stuff? I've been trying to fix it by going through help threads for hours now.

My computer is very new, it is a sony vaio pro 13
1.5 intel core
4 gb of memory


I'm a real newbie and I'd love to have my computer working.
Thanks!

---

### Post by oldfred on 2014-01-18
You show a 128GB SSD with just Ubuntu installed. You only have old Windows boot files in the efi partition.

It does look like you installed with secure boot on as you have the signed kernels & grub.

Can you not boot ubuntu entry? And you want to make ubuntu entry first in boot order in UEFI.

 BootOrder: 0005,[COLOR=#ff0000]0000[/COLOR],0006
Boot[COLOR=#ff0000]0000[/COLOR]* ubuntu    HD(1,800,f3800,918fa951-4fe0-430f-861e-1396f0b1f3aa)File(EFIubuntushimx64.efi)
Boot0005* Windows Boot Manager    HD(1,800,f3800,918fa951-4fe0-430f-861e-1396f0b1f3aa)File(EFIBootbootx64.efi)
Boot0006* UEFI: KingstonDataTraveler 2.0PMAP    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(1,0)HD(1,3d,1e0d63,000284e9)..BO

Windows entry has no system to boot from, so it will not work.

A few systems only boot the Windows entry as vendor modifies UEFI to only allow the use of the Windows entry.

Some other Sony's
 Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
sudo -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)
Sony Vaio Pro 13 initrd issues - turn off UUID and libata.force=noncq splash parameter needed
[http://ubuntuforums.org/showthread.php?t=2189052](http://ubuntuforums.org/showthread.php?t=2189052)
Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)
Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

---

### Post by Perezvon11 on 2014-01-18
> **oldfred said:**
> You show a 128GB SSD with just Ubuntu installed. You only have old Windows boot files in the efi partition.

It does look like you installed with secure boot on as you have the signed kernels & grub.

Can you not boot ubuntu entry? And you want to make ubuntu entry first in boot order in UEFI.

 BootOrder: 0005,[COLOR=#ff0000]0000[/COLOR],0006
Boot[COLOR=#ff0000]0000[/COLOR]* ubuntu    HD(1,800,f3800,918fa951-4fe0-430f-861e-1396f0b1f3aa)File(EFIubuntushimx64.efi)
Boot0005* Windows Boot Manager    HD(1,800,f3800,918fa951-4fe0-430f-861e-1396f0b1f3aa)File(EFIBootbootx64.efi)
Boot0006* UEFI: KingstonDataTraveler 2.0PMAP    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(1,0)HD(1,3d,1e0d63,000284e9)..BO

Windows entry has no system to boot from, so it will not work.

A few systems only boot the Windows entry as vendor modifies UEFI to only allow the use of the Windows entry.


How do you suggest I get into the uefi to move 0000 infront of 0005? 

I've gone into the grub customizer and ubuntu is at the top. What am I missing?

Thank you for the reply.


EDIT 
I'm in the terminal after using efi boot manager.

I see that the order is 0005, 0000, 0006

what command do I use to get rid of 0005?

---

### Post by oldfred on 2014-01-18
You should be able to do it in UEFI menu.

 Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by Perezvon11 on 2014-01-18
Ok, So I was able to move ubuntu to the first spot. So the order says 0000 first. Still on restart it shows the vaio symbol and give me the "your vaio failed to start windows" page

I re-ran the repair, so here is a new link.

paste.ubuntu.com/6776562

maybe it is like those other system who were "hard coded" to boot windows only?

EDIT

in sda 1
/EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootx64.efi


maybe I need to get rid of EFI/boot/bootx64? 
I dont see it in the boot list though.


EDIT 
rebooted in the live usb again, installed efibootmgr, removed the windows boot efi.

After restart it went right into the "your vaio failed to start windows" page.
This means that it reinstalled the boot file on its own?

---

### Post by Perezvon11 on 2014-01-18
I've been looking at plenty of forums on people trying to install ubuntu on sony vaio pro 13.
I've reinstalled grub as shown here

[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UtsJEGTTnoE](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UtsJEGTTnoE)

Very confused. :(

---

### Post by oldfred on 2014-01-18
I think the Sony's are one's that are hard coded to only boot Windows.
 
The work around is to rename the Windows efi file to really be shim which has the Microsoft signing key and will work even if secure boot is on. Often better not to have secure boot on.

Boot-Repair will automatically do the rename if you want or you can manually do it. Since using Windows you do not have to worry about versions if Windows updates.

       Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
sudo -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)
Sony Vaio Pro 13 initrd issues - turn off UUID and libata.force=noncq splash parameter needed
[http://ubuntuforums.org/showthread.php?t=2189052](http://ubuntuforums.org/showthread.php?t=2189052)
Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)

      
 Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)


 It looks like boot repair ran its "buggy" UEFI rename function. I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.

   buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

   Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by Perezvon11 on 2014-01-18
Ok, I have gotten it to boot! Sortof...
It boots showing the ubuntu purple screen, and then goes into a black screen with a flashing _ 

after a few seconds or minutes it says "gave up waiting for root device" 

Any advice. 

Thanks for all the help!

---

### Post by oldfred on 2014-01-18
Now you are into video issues or other boot parameters. 
What video card/chip?
You may need boot parameters posted in some of the links previously posted. 

Since you only have Ubuntu, you may need to hold shift key, or with UEFI some need escape key to get grub menu to appear.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Editing the GRUB 2 Menu During Boot
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

---

### Post by Perezvon11 on 2014-01-18
Intel HD Graphics 4400

I can get to the grub menu, and I've been trying some different things, like this
[http://ubuntuforums.org/showthread.php?t=1860135](http://ubuntuforums.org/showthread.php?t=1860135)

Ill try to figure out what boot parameters are.

---

### Post by oldfred on 2014-01-19
Some other Intel boot options Each line is one that may work
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)



 (13.10) Intel graphics driver fails to manage HD 4600 on HP Split x2
[http://ubuntuforums.org/showthread.php?t=2191109](http://ubuntuforums.org/showthread.php?t=2191109)
Needed all the settings??

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

