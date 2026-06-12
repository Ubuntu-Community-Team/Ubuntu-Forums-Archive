---
title: "Grub2 Ubuntu and Windows 8.1 duel boot error - Boot-Repair failed"
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by paul155 on 2014-06-18
Hi.  I have a 64 bit HP Pavillion laptop with Windows 8 pre-installed. Windows boots using UEFI.
I have successfully installed Ubuntu 14.04, but I cannot boot directly into it.
The PC only boots directly into Windows 8 (does not launch grub). The only way I can get to Ubuntu is to boot into windows and hold shift and restart in Windows and then in the windows menu select the pc to restart in Ubuntu.
I have run boot-repair several times without any success.  The boot repair log is:
[http://paste.ubuntu.com/7660275](http://paste.ubuntu.com/7660275).
Any assistance would be greatly appreciated.

Hi I have found help in the following post:
[http://ubuntuforums.org/showthread.php?t=1769482&page=216](http://ubuntuforums.org/showthread.php?t=1769482&page=216)
Thread #2153
Thanks, Paul

---

### Post by oldfred on 2014-06-18
HPs seem to only boot with your method.

Boot-Repair used to auto rename the Windows boot file, but does not do that now? I prefer some of the other methods as Boot-Repair renamed the Windows boot file which later Windows will overwrite.

Several of these manually renamed boot file:
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

I prefer renaming bootx64.efi or using rEFInd.

      
 **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find renaming  /EFI/Boot/bootx64.efi  to be shimx64.efi or grubx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

   [http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub](http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub)

---

### Post by paul155 on 2014-06-19
I will try these suggested methods.
Are there any easier methods to dual boot with Windows 8 and Ubuntu, perhaps a Linux alternative to Grub2 or freeware Windows boot software that I could try?
I don't have lots of spare time to tinker, I just want Ubuntu and Windows to work.
Thanks very much for your help.

---

### Post by oldfred on 2014-06-19
Some do not want to mess with internal hard drive so they install to an external drive or flash drive. External drive can be UEFI or BIOS or even both. USB port is slower than hard drive SATA port, but system still is very usable. Best to change a few settings to reduce writes which are real slow if using a flash drive.

Is flash drive, but could be any external or could be just UEFI or BIOS.
       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

 Howto make USB boot drives 
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)

 Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it 
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

Also this video using external drive on USB3 port.
 Asus 3632QM Install on external drive with Windows 8 on internal- Irv June 2014
[https://www.youtube.com/watch?v=uOrrN-JCcQE&feature=youtu.be](https://www.youtube.com/watch?v=uOrrN-JCcQE&feature=youtu.be)

 [http://ubuntuforums.org/showthread.php?t=2229968](http://ubuntuforums.org/showthread.php?t=2229968)

---

### Post by paul155 on 2014-06-19
USB boot is certainly another option which I had not considered.
I have just booted into Ubuntu on this new HP laptop using the esc/F9 method. I didn't know about this way of doing it, so for now I will use this method.
Perhaps boot-repair will be updated at some point in the near future to fix my dual boot problem caused by Hewlett Packard.
Thanks again, Paul.

---

