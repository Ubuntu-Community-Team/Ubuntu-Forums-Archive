---
title: "Windows 10 replaces GRUB every time the computer restarts"
date: 2015-09-10
forum: Installation &amp; Upgrades
---

### Post by quiptro on 2015-09-10
Hi all,

Until recently I had a working Windows 7/Ubuntu GNOME dual boot system. I managed to do that by renaming grubx64.efi to bootmgfw.efi and replacing it with the original bootmgfw.efi in /EFI/Microsoft/Boot. This worked perfectly and I had no issues booting the two operating systems. Then came Windows 10 and I decided to upgrade. The upgrade went well, I installed Ubuntu GNOME again, replaced the original bootmgfw.efi and after rebooting I was greeted by the familiar GRUB boot menu. So far so good. Then, when I booted the system with Windows 10 and restarted it, the GRUB menu disappeared. I realized that every time I boot Windows 10, it repairs the boot loader and my GRUB menu disappears. This is very frustrating as I cannot easily switch between operating systems. If anyone can help please let me now.

Cheers!

---

### Post by oldfred on 2015-09-10
The renaming of bootmfgw.efi was one of the early work arounds. But as you found Windows updates would overwrite it. And a major grub update may write a new version and your old version is enough different that it does not work.

The other major work around now is to copy to bootx64.efi in /EFI/Boot. You still have the issue of major grub update, but UEFI will boot the default entry bootx64.efi as the hard drive boot entry. Not sure now if Windows also is resetting itself as first in boot order in UEFI and turning on secure boot as many with Windows 10 seem to have those issues also.

Work arounds, same info in link in my signature below. You may also have to add an UEFI hard drive entry. Some systems already have it. Some also find rEFInd works better, but is another boot manager to install.
       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
[/URL]
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

What brand/model system?


[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

### Post by quiptro on 2015-09-10
Thanks for your response. I tried copying to bootx64.efi but no luck. The GRUB menu shows up only during the first boot and then once I boot into Windows and restart my laptop, the GRUB is gone again.

I'm working on a Sony VAIO SVS13A190X. There are no Secure Boot or Fast Boot options in the BIOS setup. Will creating a dedicated GRUB partition do any good? Will it make a difference and put an end to my dual booting nightmares?

---

### Post by oldfred on 2015-09-10
Many Sony users have renamed the bootx64.efi.
What partition is your ESP?
If sda1 this works as that is the defaults:
 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"
OR:

 sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "Default hard drive Boot" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition 

   Codes from 
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
-c | --create
-g | --gpt
-d | --disk DISK -  The disk containing the loader (defaults to /dev/sda) 
sdX where drive sda, sdb etc
-p | --part PART -    Partition number containing the bootloader (defaults to 1)  or sda1
-w | --write-signature
-L | --label LABEL -     Boot manager display label (defaults to "Linux") 
-l | --loader NAME -     Specify a loader (defaults to \\elilo.efi) 


 One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)
      
 Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)

Some like rEFInd

 Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by quiptro on 2015-10-24
Did not work by copying shimx64.efi either. My partitions are as follows (I have clean-installed Windows 10 so the ESP partition is all gone):

Partition 1: Windows Recovery
Partition 2: EFI Partition
Partition 3: Windows Reserved
Partition 4: Windows System Partition (C:/)
Partition 5: Windows Partition (D:/)
Partition 6: Ubuntu GNOME
Partition 7: Swap

Will then the command for me be as follows?
sudo efibootmgr -c -g -d /dev/sda -p 2 -w -L "Default hard drive Boot" -l '\EFI\Boot\bootx64.efi'

Thanks for your help.

---

### Post by oldfred on 2015-10-24
When you say you clean installed Windows, is partitions as shown?
You still need Windows fast start up or always on hibernation off.
Often best to have UEFI fast boot off, just so you can get to UEFI settings. And have Secure boot off, but UEFI on. If you update UEFI from vendor you have to redo those settings as it reset to defaults.

Yes that looks correct for ESP - efi system partition as sda2. Description in quotes for entry can be anything you like.

---

### Post by quiptro on 2015-10-30
I am about to give up on dual-booting with Windows 10, it seems like an impossible task for the time being. The longest I've managed to have the dual-boot work is a couple of weeks. The solution was to replace BOTH \EFI\Boot\bootx64.efi AND \EFI\Microsoft\Boot\bootmgfw.efi with grubx64.efi. This worked until an update messed thing up. After reboot, I got the message "Operating system not found" and was not able to boot either Win or Linux. When I tried to replace the .efi files using a live-USB again, I was shocked to find out that the efi partition was locked and could not delete the old .efi files.

So I made one last Hail Mary attempt... I wiped the whole disk clean (I have all my personal files and documents backed-up) and created the following partition setup using GParted, first installing Windows 10 and then Ubuntu:

Partition 1: 100MB Linux-only EFI partition
Partition 2: 450MB Windows Recovery partition (created automatically when installing Windows 10)
Partition 3: 15MB Microsoft Reserved Partition (created automatically when installing Windows 10)
Partition 4: 100MB Windows-only EFI partition (created automatically when installing Windows 10)
Partition 5: 100GB Main Windows Partition
Partition 6: 300GB Data Windows Partition
Partition 7: 4GB Linux Swap Partition
Partition 8: 65GB Ubuntu Linux / partition

After I finished installing both OSs (Windows 10 first, Ubuntu second), I configured GRUB to boot both Windows and Linux, then restarted the system... Boot to Ubuntu -- works like charm... Restart again... Boot to Windows using GRUB -- works like charm... Restart again... SHOCK -- GRUB is gone, computer boots directly to Windows... I boot the computer using live-USB again just to find out that Partition 1 (the Linux-only EFI partition) is completely empty, all files deleted by Windows 10.

I would really appreciate if somebody could provide a sustainable solution to dual-booting win/linux as I would like to use Linux as much as possible but cannot part ways with Windows just yet because of software not available in Linux.

Many thanks.

---

### Post by quiptro on 2015-11-01
After hours spent on forums and reading various tutorials, I have found a solution to my problem. As there was no "Fast Boot" option in the BIOS of my laptop and no option to turn "Fast Boot" on/off in Power Options --> System Settings --> Shutdown Settings, I just assumed that my laptop didn't support "Fast Boot". As it turns out, not only does my laptop support it, but it had also turned it ON and hidden it from Power Options, therefore preventing me from disabling it. The solution came from the following article: 

[http://www.trishtech.com/2013/07/how-to-disable-hiberboot-in-windows-8/](http://www.trishtech.com/2013/07/how-to-disable-hiberboot-in-windows-8/)

Apparently there is a feature called "Hiberboot" present in Windows 8/10 that lets users start their systems faster than they would be started after a complete shutdown (I presume this is the "Fast Boot" thing). This feature is the reason my system couldn't compete a full shutdown and caused my laptop to boot straight to Windows. The way to disable this feature and let the system complete a full shutdown is to dig up a key called "HiberbootEnabled" in the Windows registry and set it to 0 (meaning off). The full path of the key is "[COLOR=#404040][FONT=courier new]HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Session Manager\Power[/FONT][/COLOR]".

After doing this, I can again use GRUB to choose which OS to boot (bootx64.efi and bootmgfw.efi still have to be replaced by grubx64.efi tho).

On a side note, while trying to fix this, I stumbled upon the GRUB environment variables through the GRUB command-line interface. Using the command "set", GRUB CLI lists all env vars. In that list, there is a variable called "cmdpath" whose value is set to cmdpath=(hd0,gpt2)/EFI/Microsoft/Boot/. I guess this is what causes GRUB to look for the bootloader file under /EFI/Microsoft/Boot instead of looking for the bootloader under /EFI/ubuntu. I managed to change the value of cmdpath with the command "set cmdpath=(hd0,gpt2)/EFI/ubuntu" and then "save_env". My expectation was that I could leave the original bootx64.efi and bootmgfw.efi unaltered and that GRUB would now look under /EFI/ubuntu for a bootloader and therefore start grubx64.efi directly, without me having to disguise it as bootmgfw.efi. Unfortunately, this did not work as expected. After the reboot, there was no sign of GRUB and the system booted straight to Windows. The only remaining solution is to trick the system to start grubx64.efi by disguising it as bootmgfw.efi.

---

### Post by oldfred on 2015-11-02
I believe grub cmdpath comes from UEFI.

Better to copy shim into /EFI/Boot as bootx64.efi. If in your install it will be mounted at /boot/efi or full path /boot/efi/EFI/Boot.

Copying to Windows boot file works temporarily, but Windows updates will overwrite it regularly. Boot-Repair used to change the Windows filename, but now suggests an entry in the BCD.

More info in links in my signature.

---

