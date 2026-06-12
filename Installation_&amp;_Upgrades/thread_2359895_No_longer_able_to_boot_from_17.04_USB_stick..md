---
title: "No longer able to boot from 17.04 USB stick."
date: 2017-04-29
forum: Installation &amp; Upgrades
---

### Post by twoj on 2017-04-29
I have 2 identical USB sticks;  
I installed 17.04 and was testing stick #1, and 17.04 was working fine.  Many reboots etc....

Then I created installable 17.04 on stick #2.  And once again it works just fine, boots etc...

Then I went back to booting with stick #1, and my computer does not boot??   It recognizes the usb, but it is as if there no longer is any OS on it.

I can bring up and mount stick#1 when stick#2 is up and running.  


Could it be a problem with a boot loader in the BIOS of my computer?  The were the same.  Any hope of ever booting from stick#1 again?
Any suggestions?

---

### Post by oldfred on 2017-04-29
Are these installer/live version or full installs.

External UEFI drives only UEFI boot from /EFI/Boot/bootx64.efi, so do you have that file?
Or are you booting sometimes in BIOS mode?

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by twoj on 2017-05-01
Thanks oldfred for response.

I have more info to report:
I created another installation on the stick that did not work, and it broke the stick that was working.  So I figure it has to be something in the UEFI option in my dell box.
So I went into the File Browser 'Add Boot Option'  and that allowed be to look at the files on the USB stick. Paths were:  <EFI>/<ubuntu> and in this folder:
<fw>
fwupx64.efi
grubx64.efi
grub.cfg
shimx64.efi
mmx64.efi
fbx64.efi

I tried to select grubx64.efi as one UEFI boot option, but it just sat on the dark red screen.
So it looks like the ubuntu installer creates an installation on the USB stick then it writes to the CPU's UEFI.   This may explain why one stick is knocking the other out.
 
So I may have correct installations on my 2 USB stick, just the computer can not correctly boot from them.  BTW, right now none of my sticks work  :-(



What do you think?

---

### Post by oldfred on 2017-05-01
Those files look like the standard full UEFI files in /EFI/ubuntu from a full install.

If you are trying to do full installs to a USB flash drive or any external drive, grub will not correctly install to that drive for direct booting.
With a full UEFI install grub only installs to the ESP - efi system partition on drive seen as sda.
This says triaged, perhaps because some said Boot-Repair fixes it, which I do not believe it does.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
 [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488) 

UEFI only boots from /EFI/Boot/bootx64.efi.
Grub only installs to ESP in drive seen as sda to /EFI/ubuntu.
You can manually install grub with --removable option to install to external drive, but that is not maintained by install.

You have to copy /EFI/ubuntu to flash drive. Copy again to /EFI/Boot on flash drive. Rename shimx64.efi to bootx64.efi.  And edit fstab UUID to see ESP/efi partition on flash drive not sda.
       UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad

---

