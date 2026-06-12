---
title: "How to fix Dual Boot - Windows 8.1 and Ubuntu 14.10 on XPS 15 9530?"
date: 2015-02-10
forum: Installation &amp; Upgrades
---

### Post by csete on 2015-02-10
I'm struggling to get my new laptop to dual boot Windows 8.1 and Ubuntu 14.10 properly.  I went through the installer yesterday and let it resize the partitions (500G SSD).  I did *not* disable secure boot at the time.  The installation went flawlessly and on reboot, I was presented with the GRUB menu.  I was able to log in to my Ubuntu without trouble at that point.  Later, I needed to reboot.  When I did, I was taken immediately to my Windows installation.  Since then, I've been unable to get the GRUB menu to show up again.  I've tried multiple times with boot-repair from live image, but I can't seem to get it to work.  One attempt hung the machine while updating GRUB.  The latest failed while stating "Locked-ESP detected".  At this point, I'm unsure what to try next.

The boot-repair "Boot Info Script" is available at [http://paste.ubuntu.com/10160793/](http://paste.ubuntu.com/10160793/)

Thanks for any help.
Craig

---

### Post by oldfred on 2015-02-10
Errors on sdb or flash drive and on the Intel Fast flash partition do not matter.
But grub boot files were not written into the FAT32 efi partition sda1.

Did you try to let Boot-Repair install grub to efi partition?

If you do have errors what were they. There were some efi partitions quite a while ago that were corrupted and grub could not be installed. The only repair was to backup the partition, delete it entirely. Then with gparted create a new FAT32 partition and include boot flag to make it the ESP or efi partition. Restore Windows boot files, confirm Windows boots ok and then install grub.

Best to have full backups of efi partition, and Windows before making major changes.

---

### Post by csete on 2015-02-10
Thanks for the thoughts.  I just tried taking another run at it.  Booting from live USB drive and installing boot-repair.  It was already set to install GRUB to EFI.  I told it to purge GRUB and reinstall, which seemed to get me further.  However, I'm now sitting at the grub-update dialog and have been for about 15 minutes.  The fan is running full bore and the machine is unresponsive.  I hit this point earlier today and finally forced the machine to shut down.  There is a chance I messed up my GRUB setup doing that, but I'm unsure how to proceed at this point.  I can't even Alt+F1 to get to a TTY and see what is going wrong.  Any ideas how to proceed?

---

### Post by oldfred on 2015-02-10
If doing the full uninstall/reinstall, do you have working Internet. Boot-Repair has to redownload full grub packages.

Can you just try writing a file into your efi partition to see if that is the issue?

---

### Post by csete on 2015-02-10
So far I haven't tried to do a full reinstall, only booting from Live USB and running boot-repair.  Boot-repair did have me run a bunch of commands and appeared to be downloading updated GRUB and new linux images.  I can try a reinstall if that may work better...

How would I validate my ability to write to the EFI partition?  Just touch a file from the Live USB install environment?

---

### Post by csete on 2015-02-10
I should note... this is a new machine and I have recovery disks, so I'm not too concerned with reinstalls and such... There is no data on the machine quite yet.  Although I was hoping to get this machine up soon.

---

### Post by oldfred on 2015-02-10
If you do reinstall be sure to use Something Else. Any other option may erase entire hard drive.
See link in my signature.

You can touch or just copy a file into efi partition.
Ubuntu normally has /EFI/ubuntu as a folder. Windows has /EFI/Windows with added files & folders.
Many systems also have a /EFI/Boot folder and we have to copy grub or shim into that folder and rename it bootx64.efi which is the hard drive boot entry.
Once booted into Ubuntu it mounts the efi partition at /boot/efi so full path is /boot/efi/EFI/ubuntu.

---

### Post by csete on 2015-02-11
I **think** that a new Ubuntu installation has resolved the problem.  I have to say that I'm a bit reluctant to start setting the machine up for fear that I will lose my ability to boot Ubuntu again.  Do you have any idea why I might have lost my ability to boot Ubuntu in the first place and why boot-repair was unable to fix it?

---

### Post by oldfred on 2015-02-11
Windows & UEFI often cause issues. Operating system now can change some boot parameters in UEFI.
Best to have good backups including efi partition.

---

