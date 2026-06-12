---
title: "Dual boot 12.04 and 14.04 on UEFI. Where do I install grub?"
date: 2014-01-11
forum: Installation &amp; Upgrades
---

### Post by ajgreeny on 2014-01-11
I have a superb, fast running, Xubuntu 12.04 64bit OS on my i5-3570K, HD4000 integrated graphics, 8GB ram, UEFI system.  No Windows here, other than a VM of XP on this machine for my Tomtom stanav updating application.

I now want to do a full install 14.04 as a test, (and also perhaps other Linux OSs), which I did many times on a previous old machine with legacy BIOS. Then I could easily choose to put grub on a partition instead of the MBR when installing the second OS, thus keeping the running grub from the default main OS.  If I later wanted to use the second OS as the default I could simply boot to that and run ```
sudo grub-install /dev/sda
``` Now with UEFI I think that command needs changing as grub no longer seems to be on the MBR as it was in BIOS, but I do not know what that new command should be.  How about using the /dev/sda1, which is my efi partition instead?

I imagine I could use boot-repair, but that is also something I do not know, have never used, and therefore do not trust mtself to use successfully.

So if I have a Linux OS as a second option on my machine, can I run a simple command like the above to put that second OS's grub as the controlling grub for booting my machine?

---

### Post by ubfan1 on 2014-01-11
The UEFI way to handle multiple bootloaders is to simply put them into a different directory in the EFI partition (/EFI/ubuntu/grubx64.efi, etc.), but regardless of location, grubx64.efi (by default anyway) looks in /EFI/ubuntu for the grub.cfg file.  Now in 12.04, this grub.cfg file might have been an actual copy of a full grub configuration, but later distributions made the file a stub which pulls in the maintained copy out of /boot/grub.  You can experiment with multiple EFI partitions (only one bootable at a time), but why not just install 14.04, and boot it off the grub menu from the 12.04 root.  Then when you want to switch over to maintaining grub from the 14.04 root, just edit the /EFI/ubuntu/grub.cfg to change the disk designation.

---

### Post by oldfred on 2014-01-11
I might backup efi partition and just install the new 14.04 to sda which will overwrite the older efi files in sda1. 
I also have seen users with kubuntu as another folder in UEFI, so it becomes another UEFI boot entry. 

But probably just easier to run sudo update-grub and boot from default grub that comes up. 

I think ubfan1's comments may explain why some users with special formats have had to add another grub.cfg with a single configfile entry to the actual grub.cfg as then grub did not pull in the correct path to grub.cfg in install.

---

### Post by ajgreeny on 2014-01-12
Thanks for those suggestions.

So, you seem to be saying that there is no equivalent to the command **sudo grub-install /dev/sda** now that we have moved to UEFI instead of legacy BIOS.

Where does grub actually reside now that it's not on the MBR of a hard disk?  Is it sitting in the efi partition?  I'm confused.  And if it's in the efi partition can we not use **sudo grub-install /dev/sda1**, sda1 being my efi partition?

Presumably if I use the "Something Else" option when installing one of the ubuntu family I can still choose to put grub on the new OS partition, and then simply run **sudo update-grub** on the primary OS to add the new OS to the menu.

---

### Post by ubfan1 on 2014-01-12
Grub may be anywhere in the EFI partition, since its location is typically specified by the nvram entry to the location.  The grub executable is named grubx64.efi (two versions exist, but you are not concerned with the signed version, nor with shim.efi)  The one exception is putting a copy of grub.efi into /EFI/Boot/bootx64.efi, which normally does nothing, but may be a failback option when a nvram boot attempt fails. I use secure boot, and since I keep losing my shim.efi nvram entry, I can still use the old grub entry, (which cannot boot, since it is not signed by Microsoft) which fails, but then the bootx64.efi attempt is made, (and in my case, it's a copy of shim.efi), so the boot still works.  Using the partition on the grub-install should work, but I have seen it fail when using an external EFI on a USB device.

---

### Post by oldfred on 2014-01-12
The sudo grub-install /dev/sda with UEFI will automatically put efi boot files in the efi partition. But you need to be in UEFI mode. I think saying sda1 installs to the same efi partition as with UEFI there is only one place to install.

Depending on mount path these two files should be in the efi partition in an ubuntu folder. Not sure what else is there. When mounted in UEFI install it is /boot/efi, and from external mount it is without the /boot/efi.
  /boot/efi/EFI/ubuntu/grubx64.efi 
/boot/efi/EFI/ubuntu/ shimx64.efi

---

### Post by ajgreeny on 2014-01-13
Oh gosh!  Confusing isn't it.

I understood grub and how to deal with it on a multiboot with five OSs using a legacy BIOS/MBR system, but suddenly I appear to be right at the bottom of the knowledge ladder again as far as UEFI is concerned.  It does seem from oldfred's last comment, however, that the **sudo grub-install /dev/sda** may still be all that is needed, so I may try it when I eventually do a clean install of 14.04, but I think for the moment at least I will stick with the VM of 14.04, and keep that fully updated just to see how the new LTS version is working.  So far it has been brilliant, and is hard to believe it is a VM as it runs so well.

Thanks for your help and comments.  To quote the old adage "If it ain't broke, don't fix it!"

---

