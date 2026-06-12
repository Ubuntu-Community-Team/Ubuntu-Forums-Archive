---
title: "Dual boot Windows 8/Ubuntu 12.10 won't load grub"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by abdalalim1982 on 2013-03-07
My wife has an HP Pavilion g6-2279wm.  I created a partition to install Ubuntu 12.10.  I turned off the secure boot, but it boots straight into Windows.  I ran boot-repair from a live usb, and it gave me this url:

[http://paste.ubuntu.com/5594594/](http://paste.ubuntu.com/5594594/)

Any assistance would be much appreciated.

---

### Post by x64Architecture on 2013-03-07
[COLOR=#000000]- boot with Ubuntu (live version, from the USB key), and use GParted to change the flag of the EFI partition : remove the boot flag.[/COLOR]
[COLOR=#000000]- shut down the PC, remove the USB key, and boot with windows 8 (the removal of the boot flag does not prevent windows to boot).[/COLOR]
[COLOR=#000000]- within windows 8, call the partition tool (search for "partition" in the control panel or in the parameters setting search tool). [/COLOR]
[COLOR=#000000]- in the partition tool, select the EFI partition, and give it a Drive letter (you can do it because it is not anymore marked as a "boot" partition).[/COLOR]
[COLOR=#000000]- then open a File Navigator, and go to the Drive of the partition : you can see the EFI folder, and navigate down to the file : /EFI/ubuntu/grubx64.efi[/COLOR]
[COLOR=#000000]- suppress the file.[/COLOR]
[COLOR=#000000]- shut down the computer[/COLOR]
[COLOR=#000000]- restart with Ubuntu (live version, from the USB key), and use GParted to change the flag of the EFI partition : set back the boot flag.[/COLOR]
[COLOR=#000000]- install the Boot Repair tool (see here above, and the link to the Boot Repair page).[/COLOR]
[COLOR=#000000]- proceed to the repair : choose your settings and option, etc...[/COLOR]
[COLOR=#000000]- the process should be success-full, and the Ubuntu Grub panel appear when starting.[/COLOR]

[COLOR=#000000]Taken from - [/COLOR][http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273)[COLOR=#000000]

[/COLOR]

---

### Post by abdalalim1982 on 2013-03-07
I attempted to do the above, but when I go to the drive, there is no ubuntu folder in the EFI folder.  I am assuming that this is the main issue here.

---

### Post by oldfred on 2013-03-07
Some computers seem to have a write protected efi partition. Which as far as I know is not possible with FAT32. Several work arounds posted. Previous poster had one of them. There may be some sort of setting in UEFI, but no one has posted it. Sometimes setting that you do not think applies do apply. For example in BIOS system a user could not get it to work and he had floppy turned on in BIOS but had no floppy. 

Best to fully back up efi partition before all the experiments. 

 grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
Some find chkdsk on efi partition helps, others backup, reformat and restore as current work arounds.
Another possible work around. HP Pavalion G7
[http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273)

---

### Post by abdalalim1982 on 2013-03-24
I tried reformatting the efi partition, and placing the files back in there.  I then ran boot-repair, at which point it had me type commands into terminal to download signed efi files and install them.   I got the following: paste.ubuntu.com/5644637.  I rebooted, and still straight into Windows 8.  Sorry about the delay in posts, but I have been very busy.

---

### Post by oldfred on 2013-03-24
With gparted you set the boot flag on the efi partition. It really is not the same with gpt partitions, as it really makes the partition the efi partition. All systems boot from the efi partition and you can only have one per drive.
Change sda2 to efi with boot flag in gparted.

Did you run the fixes suggested by Boot-Repair?

---

### Post by annnomius on 2013-03-25
did you do this in windows 8?:
open the control panel, choose system &  security-->power options-->choose what the power buttons  do-->change settings that are currently unavailable-->**deselect**  "turn on fast startup".

::ann

---

