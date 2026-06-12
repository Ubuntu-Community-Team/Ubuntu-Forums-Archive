---
title: "Dual boot issue: Ubuntu 12.04 &amp; Windows 8, unable to boot Windows (Laptop Asus K75VM)"
date: 2014-11-30
forum: Installation &amp; Upgrades
---

### Post by hannu-kamarainen on 2014-11-30
(A separate thread from [http://ubuntuforums.org/showthread.php?t=1769482&page=222&p=13176998#post13176998](http://ubuntuforums.org/showthread.php?t=1769482&page=222&p=13176998#post13176998))

Hello,

thank you for the great software that is boot-repair, it has saved me from a pinch before. This time I've got a problem though that boot-repair could not be solve.

Basically I have dual boot laptop with Ubuntu 12.04 and Windows 8, but only Ubuntu is booting.

The options available for booting Windows either only lead back to the boot menu, or briefly display a loading screen (twice) for "Windows is loading files", and then proceeds to reboot the machine, leading back to the boot menu again.

The problems initially started without me taking any specific action, possibly after either Ubuntu or Windows updated itself (although I don't remember doing either explicitly..) and later starting up the computer. And here we are.

Details after running boot-repair here [http://paste.ubuntu.com/9299810/](http://paste.ubuntu.com/9299810/)

Any input on how to proceed to solve this problem would be greatly appreciated.

Regards, Hannu 

-----------------

Update:

In response to [http://ubuntuforums.org/showthread.php?t=1769482&page=222&p=13177009#post13177009](http://ubuntuforums.org/showthread.php?t=1769482&page=222&p=13177009#post13177009)

Laptop is ASUS, model K75VM.

I ran boot-repair again, without using secure boot mode, the result is still that Ubuntu boots, but Windows does not. New details from running boot-repair: [http://paste.ubuntu.com/9316628/](http://paste.ubuntu.com/9316628/)

Indeed previously I have had a problem where only Windows was booting as well. I tried renaming the bootmgfw.efi.bkp, but it had no effect. Also, the .efi file that is being used in the menu entry "Windows UEFI bootmgfw.efi" was using bootmgfw.efi, and not .bkp, which I understand is the actual Windows boot file. If not manually changed, the original entry will only lead to the same menu screen again.

I attempted a similar solution as was explained in this post [http://ubuntuforums.org/showthread.php?t=2101840&p=12440378#post12440378](http://ubuntuforums.org/showthread.php?t=2101840&p=12440378#post12440378) and made a new menu entry in /etc/grub.d/40_custom and set the root manually to hd0,gpt1 and use bootmgfw.efi.bkp. No success.

I also tried making a new boot entry in BIOS to start from EFI/Microsoft/Boot/bootmgfw.efi.bkp, but all that ever tries to boot Windows results to this short "Windows is loading files" screen with a small loading bar, and then reboots the machine. This appears to me that Windows seems to be found and tries to boot, but something else is wrong, though I am unable to find previous cases of a similar issue?

-Hannu

---

### Post by oldfred on 2014-11-30
I think Asus also require one of the work arounds. 
Renaming bootmgfw.efi was the original work around and used by Boot-Repair. Also back then grub2's os-prober did not find a correct UEFI boot for Windows, just the old BIOS boot stanza which never would work with UEFI.
So Boot-Repair renamed the Windows efi file and created a new boot stanza 25_custom to boot the renamed Windows file. It used 25_custom just to make it first on menu. Your 40_custom should work the same way. A few users did the same thing manually.

But part of issue then is Windows updates will overwrite bootmgfw.efi and then you are back to booting only Windows. And major grub updates will write a new grubx64.efi and that needs to be copied again. Or lots of maintenance and understanding of what files are where and which is most current version.

Other alternatives since discovered that work. 
       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
[/URL]
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

I suggest a full backup of the efi partition and we start over.
First we get Windows booting directly from UEFI menu, then do a work around that requires less maintenance.
The issue may be that you left Windows in hibernation or fast boot left on. Grub cannot boot Windows if that is the case. And grub really only boots working Windows, so better to be able to directly boot Windows from UEFI menu if needed and have a separate Windows repair flash drive to make Windows fixes if you cannot boot Windows at all.

So first rename the bkp file back to bootmgfw.efi and from UEFI see if you can directly boot Windows. Or copy bootmgfw.efi from c: or main Windows install.
If Windows boots make sure fast boot is off. And generally better to have secure boot off.

       
 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://mjg59.dreamwidth.org/24869.html](http://mjg59.dreamwidth.org/24869.html)

    
These were Windows 7 but UEFI, so they do not have secure boot nor fast boot issues.
Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[http://ubuntuforums.org/showthread.php?t=2251167](http://ubuntuforums.org/showthread.php?t=2251167)
      HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)             [ ]("http://ubuntuforums.org/showthread.php?t=2234019")

---

### Post by hannu-kamarainen on 2014-11-30
Fantastic, thank you so much, problem solved.

I copied over C:\Windows\Boot\EFI\bootmgfw.efi and placed it in /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi, ran update-grub, and that was it.

On Windows, fast-startup was indeed on, but as far as I can remember, the last time before the problem surfaced, I was using Ubuntu, not Windows. Turned off fast-startup now anyway to be more secure.

Do you have any recommendations to future-proof my system? I was thinking of simply making separate boot entries for both os'es in the bios, and override the boot-option to Windows when I need it. As I understand, this way the updates in grub and Windows don't affect each other?

-Hannu

---

### Post by oldfred on 2014-11-30
The most common fix seems to be copying grub into /efi/Boot and renaming it to bootx64.efi. That would require updates if grub had a major update, so you would have to keep track of versions.

I thought with Asus Windows liked to reset itself to be first or only boot choice. Was yours originally Windows 7, as those UEFI did not seem to have the vendor modifications to only boot Windows.

Most users seem to be using the rename of bootx64.efi
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

The efibootmgr rename of grub to Windows only works if not booting Windows. But if rarely booting it, you could run a rename to/from grub or Windows actual file.
I do not suggest B: or a2 anymore.
UEFI also has a one time boot. I think that is what editing the BCD entry C: does. You boot into Windows then set UEFI for one time reboot and then reboot thru UEFI into Ubuntu.
Not expermented with rEFInd, some some say it works. But then it is another boot manager. UEFI is a boot manager, grub is both a boot manager & boot loader.


 modprobe efivars
sudo efibootmgr -v
      
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
> BootNext - the boot entry which is scheduled to be run on next boot.
  This superceeds BootOrder for one boot only, and is deleted by the
  boot manager after first use.  This allows you to change the next boot
  behavior without changing BootOrder.

    
It looks like this is the one time boot:
-n | --bootnext XXXX  set BootNext to XXXX (hex)

If you set XXXX to Windows, then it should boot Windows once?

---

