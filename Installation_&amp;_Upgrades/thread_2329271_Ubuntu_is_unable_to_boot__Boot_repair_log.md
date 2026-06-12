---
title: "Ubuntu is unable to boot / Boot repair log"
date: 2016-06-29
forum: Installation &amp; Upgrades
---

### Post by kristianisdms on 2016-06-29
Hi All

I am new to ubuntu, but after too much Win10 nagging, I installed Ubuntu on my Sony Vaio. It worked great for a few weeks, until it didn't.

When I attempt to boot, the VAIO recovery center opens up, and tells me it cant find a bootable version of Windows. I have used Ubuntu Live to install Boot Repair, which creates the following log:
[http://paste2.org/hbXEWvUD](http://paste2.org/hbXEWvUD)

What is my issue, and how can the install suddently go from working, to being unable to boot without any apparent reason?

I hope you can help me, thanks.

---

### Post by oldfred on 2016-06-29
Did you leave it hibernated?
I do not know hibernation as system always boots very fast without it, so never have used it.

You show no NTFS Windows partitions.
You have some older entries in UEFI's NVRAM for Windows. One boots Redhat and one boots Windows efi files, neither of which are anywhere on system.
You do not show a /EFI/ubuntu folder with Ubuntu/grub's efi boot files?

But Sony usually does not directly boot anything other than Windows anyway. It is hard coded to boot by description and only valid description is "Windows Boot Manager".  
You have to do like you did with Redhat and rename the ubuntu entry for grub or shim to be "Windows" or add a fallback/harddrive boot entry that boots from a UEFI: hard drive type entry. I suggest adding both.

Make sure you have run the full un-install/reinstall of grub with Boot-Repair, so you have /EFI/ubuntu.

 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options.
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178) 
     
I would delete the two "Windows" entries in UEFI's NVRAM and add a new one to boot grub/shim.
sudo efibootmgr -v
       Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B 

 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr) 

New "Windows" entry to boot shim.
      If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by kristianisdms on 2016-07-03
Thanks a lot for this tip! - It worked.

BUT, when ubuntu downloads and installs an update, I am back to square one. I have to delete the windows boot entry and create a new one once again.
Any clues as to why this happens?

Best regards

---

### Post by oldfred on 2016-07-03
A major grub update may create a new UEFI entry and make it first in UEFI boot order.
But your Sony will not boot a description like 'Ubuntu'. 
But it should not be changing on every update, unless something else is going on between Sony's UEFI and anything that is not "Windows".

Do you have the "Windows Boot Manager" using shim?
Post this:
sudo efibootmgr -v

The other work around is to copy /EFI/ubuntu to /EFI/Boot and rename shimx64.efi to bootx64.efi.
The /EFI/Boot/bootx64.efi entry in the ESP is the default drive boot or a fallback boot entry. 
All installers use that name for your external flash drive and it can be used for an internal drive.
But then you are booting something like UEFI:hard drive or similar entry.
       Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

---

