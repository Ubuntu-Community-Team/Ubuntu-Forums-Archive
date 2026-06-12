---
title: "Alternative way to repair boot after installation on Windows 8"
date: 2014-06-11
forum: Installation &amp; Upgrades
---

### Post by tetelee on 2014-06-11
I understand that after Ubuntu installation (I installed 14.04 LTS) on a Windows 8 machine it is highly possible that the GRUB2 is still not configured as master boot and it goes directly to Windows 8 (it is also my case). It is mentioned that the solution is to run boot-repair tool using the live session on CD/USB stick. Unfortunately I can't achieve so I was wondering if there is a way to do such repair in terminal without desktop?

The reason I can't run boot-repair is because I can't have a desktop session at all: because I have hybrid graphics (Intel/ATI) on my laptop and it can't configure the graphics card properly. It says "The system is running in low-graphics mode". The solution to that seems to be re-install the ATI drivers but, as you can guess, since I am only running it from my USB stick, the installation won't take any effect because nothing really gets installed. Some post suggest to disable the ATI graphic card in BIOS temporarily, but sadly it can't be done either because my BIOS is a locked version (InsydeH20 2.13) from the manufacture which doesn't give me such option.

So my thought is, I can have some way to modify the boot from terminal of the live session on USB (that I can do). And after I have configured the boot correctly and succeeded in running the Ubuntu from my HDD, I can install the correct drivers (in recovery mode) on my machine so that the graphics card can be configured correctly. But can I configure the boot now?

---

### Post by oldfred on 2014-06-11
With many systems, you still need to go into UEFI menu and choose which system to boot. Also many have a one time boot key that will show both Ubuntu & Windows as well as DVD or flash drives if also bootable.

If in low graphics in your install, you can just use terminal to install correct graphics driver.  three keys at once - cntrol-alt-t
Often you can get into system with nomodeset on grub menu.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    
But you can use chroot or CHange ROOT to boot from your live installer but change to work into your installed system.
Boot-Repair actually walks you thru a chroot to do a full uninstall/reinstall of grub or to convert a BIOS install to UEFI install. While in chroot you can run additional commands.

---

### Post by tetelee on 2014-06-11
> **oldfred said:**
> 
Boot-Repair actually walks you thru a chroot to do a full uninstall/reinstall of grub or to convert a BIOS install to UEFI install. While in chroot you can run additional commands.

Thanks for your reply. I thought that there should be a command-line method which ultimately does the same thing as boot-repair. But in fact I solved it by using a tool in Windows. The fact is after installation, the boot loader file (.efi file) was indeed created and stored in the EFI system partition (ESP), but was jut not used. Windows has a tool called `bcdedit` which can configure the boot manager. Basically I followed the guide [http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub](http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub)

in first answer's second suggestion. I use shimx64.efi and it works. 

As for the low-graphic problem, I don't have it in the OS I installed (it seems I only have it from the live USB boot. I don't know why but I am glad it is all solved.

---

