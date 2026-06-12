---
title: "Windows 8 Dual Boot not Working"
date: 2015-05-13
forum: Installation &amp; Upgrades
---

### Post by nathan74 on 2015-05-13
Good Morning all. 

I have been trying for a while now to try and boot Ubuntu 14.04.2 alongside my version of Windows 8. I have Ubuntu installed, but the boot manager fails to open it saying I'm missing a file "EFI\ubuntu\shimx64.efi". I've tried various solutions, most recently booting from the USB and running boot-repair. I ran this twice, once with secure boot on and once with it off. My most recent run (with secure boot off) generated the file "http://paste.ubuntu.com/11114052/". Any help fixing this issue would be greatly appreciated.

Thanks you much

---

### Post by oldfred on 2015-05-13
Is this yours?
[http://paste.ubuntu.com/11114052/](http://paste.ubuntu.com/11114052/)

HP is one of several that modify UEFI to only boot by description the Windows entry. 
If dual booting we have copy shim or grub to /EFI/Boot and rename to bootx64.efi. Then you can boot a hard drive entry from UEFI boot menu. See also link in my signature for more details.

You should be able to also do the fix Boot-Repair suggests in adding an entry to Windows BCD.
Some also use rEFInd.
       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it also rEFInd
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

            HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

    

Boot-Repair added a lot of HP's efi files into 25_custom. It makes for  a lot of grub boot menu entries. You may want to either turn off execute bit on that file or backup & edit it.
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/25_custom_backup
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/25_custom_backup
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by leunam12 on 2015-05-13
Did you go through the guide for installing Ubuntu UEFI mode? What computer is this? On my computer I had to disable "MSI Fast Boot" at BIOS to be able to boot; I know this only applies to MSI motherboards, but maybe there is a similar setting for your particular motherboard.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

