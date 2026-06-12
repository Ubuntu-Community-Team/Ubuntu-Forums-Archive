---
title: "Installing full Ubuntu on an SD card (Surface Pro 2 issues with Grub)"
date: 2016-01-18
forum: Installation &amp; Upgrades
---

### Post by thomas86 on 2016-01-18
Hi all,

I am trying to install a full Ubuntu into an SD card without touching anything from the windows SSD (not dual boot and not touching the Windows boot-loader)

-Within Windows10 I installed Ubuntu 5.10 into a USB flashdrive via Universal-USB-installer
-Deactivated the Secure Boot Control on the Surf Pro 2 BIOS
-Booted into the USB flashdrive (holding the Vol-Down and Power button technique to get into the Grub menu of the SurfacePro2)
-Used the USB flashdrive to install full Ubuntu into a high speed 32Gb SD card (I created two partitions in the SD card; a main and a swap)
-The operation was a success at first. The very first boot into the SD card was successful (using the Vol-Down and Power button to get into the GRUB menu).

After shutting down the SDcard session, it was no longer possible to boot into it; the Vol-Down and Power button method no longer worked. Surface Pro keeps booting straight into Windows. I can reinstall Ubuntu into the SDcard and again it will boot once. Reinstalling GRUB via the live USB is ineffective (plus I didn't do anything to knock it off in the first place)

I must have missed a step (since most tutorials do not expect full installation into an SD card). Could someone help ?
(Please try to be descriptive because I am not a power user. Also, keep in mind I have no wifi access while inside Ubuntu; I am in the process of manually upgrading the kernel to 4.3 which might solve the wifi issue, once I manage to boot into SD card)

---

### Post by slickymaster on 2016-01-18
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by Tom_S. on 2016-01-18
The reason why it's working once is that the USB flashdrive with the installer has a boot loader installed correctly, but the SD card doesn't.

Your SD card only has a main (root) and a swap partition; it needs an EFI partition as well. The Ubuntu installer is also a large part of the problem, it will put the bootloader onto the Surface SSD even if you tell it to put it onto the SD card.

I had the exact same problems installing onto a microSD card on my  Surface Pro 3, so after getting help on the forum, I wrote up a complete procedure here:  [http://ubuntuforums.org/showthread.php?t=2309963](http://ubuntuforums.org/showthread.php?t=2309963) A little long-winded,  but thorough. Not sure if it will apply exactly to the Surface Pro 2, but it might be a good starting point.

If you use the latest version of Ubuntu you might have better support for Surface peripherals like WiFi. Eg. v14 doesn't support the Surface Pro 3 Type Cover but v15 does.

Interested to hear if it works for you...

---

### Post by thomas86 on 2016-01-20
Thank you for the detailed instructions.
I have been at this for the past three days and there is still no resolution (it is possible that Surface Pro 2 is slightly different enough to drive me crazy, or I keep missing some detail)

Copying the EFI files from the hard drive to USB (as listed in Tom_S instructions) did not really do anything for my case. It kept booting to GRUB and it would not boot without the USB installed.
I had to go in efibootmgr and change the boot order to Windows first, but now it only boots windows (I can only get to Ubuntu of I fully load windows and then go to recovery and choose Ubuntu from there)
Also, the Surface Pro boot functionality is now broken. Using the VolumeDown+Power will boot windows both ways.

So many things have gone on. I have reinstalled Ubuntu at least a dozen times; the very last one because I realized the USB partition table must be in GPT style for the EFI partition to be meaningful.
Updating the Ubuntu Kernel knocks off the EFI all over again (I had to go for kernel 4.3 in order to gain wifi that doesn't freeze the system). I also tried reinstalling Windows 10 in hope that it will fix its own bootloader, but it didn't)

Overall, I have a working Ubuntu installation that doesn't boot properly and a Surface Pro that no longer obeys the VolDown+Power thingy.

PS: I didn't understand the need for this instruction "**[B]bootrec/fixmbr**[/B]" (in Tom_S' list) because windows10 does not use an MBR as far as I understand it (MBR relates to old BIOS technology not the new UEFI stuff)

---

### Post by thomas86 on 2016-01-20
Ok, after using EasyUEFI now I see what is happening--> [http://www.easyuefi.com/index-us.html](http://www.easyuefi.com/index-us.html)  

[ATTACH=CONFIG]266848[/ATTACH]

Once I create a boot entry for the SD card and put it on the top of the boot order, everything works. It correctly boots into GRUB upon restart. 
HOWEVER, once the SD card is removed and the system is booted into Windows, the SD card's boot entry is deleted automatically and it never re-appears unless we go back in efibootmgr or EasyEFI and recreate it.

I have no idea how to make a persistent boot entry.
Also it baffles me that when my Ubuntu live USB stick is attached and I do the VolumeDown+Power thing it is recognized and gets into GRUB, but my USB stick with the full Ubuntu is giving me so much grief. I don't get it.

---

### Post by oldfred on 2016-01-20
Even if you remove a hard drive, UEFI loses its saved entries in NVRAM.

Some reread the ESP - efi system partition and add new entries on full cold reboots. But most Windows systems default to a fast UEFI boot (different than Windows fast start) to speed boot. It assumes all hardware & settings are the same, which is normally ok, but not if dual booting, or changing system. Some also require specifically allowing external devices to boot in UEFI settings, especially with Secure boot on. It is often assumed that Secure boot will not allow any external device to boot as that is not secure.

Also external devices like flash drives or external drives use a fallback or default UEFI boot entry that is /EFI/Boot/bootx64.efi. Many systems have that entry and it is just a copy of Windows efi boot file. For many systems we just copy shimx64.efi from /EFI/ubuntu/ to be that file  & then Ubuntu will boot. you may have to still add an entry into UEFI's NVRAM for the device if not found.

Try copying all of /EFI/ubuntu to SD card's ESP from internal drive. Then copy shimx64.efi to /EFI/Boot/bootx64.efi on SD card. The version of grub that you copy expects to find files in /EFI/ubuntu so you must have that. A live installer's UEFI version of grub has whatever files it needs, so does not have the same configuration.

May be similar even though newer model:
 Surface Pro 3 - USB/MicroSD Only Install 
[http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798](http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798)
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)

 Surface Pro2 mega thread:
[http://ubuntuforums.org/showthread.php?t=2183946](http://ubuntuforums.org/showthread.php?t=2183946)
[http://ubuntuforums.org/showthread.php?t=2209247](http://ubuntuforums.org/showthread.php?t=2209247)

---

### Post by thomas86 on 2016-01-20
"*Try copying all of /EFI/ubuntu to SD card's ESP from internal drive.  Then copy shimx64.efi to /EFI/Boot/bootx64.efi on SD card. The version  of grub that you copy expects to find files in /EFI/ubuntu so you must  have that. A live installer's UEFI version of grub has whatever files it  needs, so does not have the same configuration.*"

That was the first thing I did three days ago. 
All the problems I've been having are after the EFI steps were completed.
The SD card EFI already contains a Boot and a Ubuntu directory with the files as you described, but none of it matters because the NVRAM is reset whenever the SD card is removed and never defaults to /EFI/Boot/bootx64.efi unless I explicitly make an entry with that path manually. (Something about Windows BCD resetting the NVRAM entries each time Windows boots).

I don't know what else I am missing.

---

### Post by thomas86 on 2016-01-20
FIXED ! FIXED !

OldFed was right but I still managed to confuse myself.
The structure of the EFI on Windows 10 is such that there is a /Boot directory and an /EFI/Boot directory; taking from that cue I was creating a /Boot in the SD card's EFI partition (not SD Card's /EFI directory)

The HDD EFI partition (The outside /Boot directory is what caused all the confusion)
[ATTACH=CONFIG]266860[/ATTACH]

The Correct EFI partition structure on the SD card (The /Microsoft directory is probably not needed in there; I put it to test why the boot fails if Windows is selected at GRUB menu)
[ATTACH=CONFIG]266861[/ATTACH]

---

### Post by oldfred on 2016-01-20
Glad it worked.

Paths can be a bit confusing as from Ubuntu booted it mounts the ESP at /boot/efi so full path is 
 /boot/efi/EFI/ubuntu, but if mounting from live installer it will be different. In FAT32 case like Boot or BOOT or boot are all the same.
And standard paths as you show above, depending on configuration:
      
 Boot files:        
/efi/Boot/bootx64.efi 
/efi/ubuntu/grubx64.efi
/efi/Microsoft/Boot/bootmgfw.efi

---

