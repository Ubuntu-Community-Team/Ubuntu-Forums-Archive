---
title: "Dual boot ubuntu and windows 8"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by wildmanne39 on 2013-03-08
Hi, I bought a new gateway laptop with windows 8, is this one of the computers that Ubuntu can be dual booted on? if so can someone please give me the directions I will need to install Ubuntu as a dual boot.
Thanks

---

### Post by oldfred on 2013-03-08
Have not seen any Gateways yet. What model and whose UEFI/BIOS? There are only 4 or 5 UEFI vendors, but each is customized by the vendor for each model computer.

Is this an UltraBook? That complicates it as it will have dual video needing bumblebee and has RAID which has to be turned off.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by wildmanne39 on 2013-03-11
Hi oldfred, it is a gateway NE56R47u, I do not know who the vender of the UEFI/BIOS is but I will find out, I would have done a lot of research before posting but I am on my cell phone while I am on the road and it makes it very hard to use and see the internet.

I will be home in a couple of days then I will get started on installing Ubuntu on it.
Thanks very much.

---

### Post by oldfred on 2013-03-11
It is not an Ultra-Book. While Intel graphics only has one open source driver, some seem to have issues with it. There may be extra settings required, If UEFI is reasonably correct then it should install ok.

---

### Post by wildmanne39 on 2013-03-15
I am trying to boot from the usb stick but it does not even show up in the list of boot devices, does it need to be formatted for windows in order for it to be recognized? 

Hi, usually do not have trouble booting usb sticks but I have never tried it with windows 8 before now.

I have not found away to disable fast boot.
Thanks

---

### Post by oldfred on 2013-03-15
Ubuntu will boot either UEFI or BIOS from a UEFI menu. But you have to have installed Ubuntu as a bootable install. I only have BIOS but I only see my flash drive under the choices of hard drives, not any USB boot options.

A Windows repairCD required special effort to convert to UEFI boot.
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by wildmanne39 on 2013-03-15
I finally got the usb stick to boot with secure boot off but I will have to get it to work with secure boot on before I can install it or it will not boot correct?

There is an EFI boot partition for windows.
Thanks

---

### Post by oldfred on 2013-03-16
Some systems only work with secure boot off. Others will work with it on or off. Not exactly sure what UEFI differences there are that cause that as grub2's new shim file has the same Microsoft key that will work with secure boot systems. But some vendors make other changes to UEFI to only boot Windows.

Some examples of vendors modifing UEFI incorrectly.
 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

A major work around that Boot-Repair does for those that only boot the Window's efi boot file.
      
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

---

### Post by wildmanne39 on 2013-03-16
The good news is ubuntu and windows 8 will both boot after install if I change  EFI to bios legacy and back to EFI for 
windows.

I have not tried to get into the grub menu yet but that is on the list for next thing to do.
Thanks for all your help, if you have any suggestions for having to switch EFI to bios legacy to boot ubuntu and then back 
to EFI  to boot windows 8 I would appreciate it.

---

### Post by oldfred on 2013-03-16
Both have to be in the same mode to easily dual boot. BIOS & UEFI write system parameters differently, so you cannot boot unless same.

But Boot-Repair will convert a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi. The small bios-grub partition used for BIOS boot with gpt partitioning then can be deleted.

Grub2's os-prober does not create correct chain load entries either. So you need Boot-Repair to fix that with correct efi entries in 25_custom.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    
Until grub fixes os-prober, you might as well turn off os-prober.

       # I add this line to grub configuration or turn off the execute bit on 30_os-prober
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub

---

