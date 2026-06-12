---
title: "Unusual dual boot configuration (questions from a linux newb)"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by CZStover on 2008-08-01
I will be installing a fresh copy of vista in the near future and would like to dual boot with Kubuntu, but I have a bit of a(somewhat) unusual situation.  Here's what I would like to do...

I have 4 SATA drives.  I would like to put Kubuntu on 1 drive, put Vista on 2 of the drives in a mirrored RAID using Intel Matrix, and make the 4th drive a backup/media drive. 

I've read some information regarding dual boot installations but haven't come across anything that addresses my situation.  So here I am with my hat in my hand asking help from you fine folks!!

Thanks in advance!!

---

### Post by logos34 on 2008-08-01
I'd recommend making the first disk of the raid array the Bios boot drive, and making sure to plug in your disks to sata channels 0-3 on the motherboard to match the bios boot order.  So raid drives on 0 and 1, ubuntu on 2, etc.  Install ubuntu but at step 7 "ready to install' screen hit 'advanced' button and replace grub location '(hd0)' with the boot raid drive, /dev/sda, just to make sure it goes to the correct drive.  Grub will overwrite the windows bootloader.

This seems to me preferable to having linux as the boot drive, in which case grub may have problems performing a virtual swap of windows due to raid arrangement (windows will not boot otherwise)

---

### Post by CZStover on 2008-08-01
Hmm, sounds reasonable...  So grub won't have any problems being installed on the windows raid drives?  I was under the impression that linux didn't view "software raid" in the same fashion as windows.  Is this not the same for grub?  If grub overwrites the vista bootloader, won't that screw up the raid array?

---

### Post by logos34 on 2008-08-01
you can always reinstall the windows boot loader from the vista dvd if it doesn't work.  I'm not saying grub won't have trouble correctly identifying the raid array, I'm just trying to eliminate the potential problem of booting windows from a non-first location, which raid may complicate.  

That said, on second thought the easiest thing to do would probably be to install and configure the windows raid, then once it's working ok, set the target ubuntu drive to **first** position in the Bios **hard disk boot priority**, install ubuntu, and let it write the grub bootloader to the default location ('hd0' in this case should work since it's set as the boot disk in the bios, but you could always use '/dev/sd?' format to be sure).  Hopefully it will detect the windows installation and add the appropriate entry (with [mapping]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")__) to /boot/grub/menu.lst.

If it works, fine...if not you can always just toggle the Bios hard disk boot order whenever you want to boot the other OS.

---

### Post by CZStover on 2008-08-02
Alrighty, thank you tremendously for your help so far.  If grub does not recognize the raid array, is there a way to manually add it in?  What would/will happen if (more like when with windows) I need reinstall a corrupt copy of vista?

Sorry for all the questions, it's just that the last time I tried to install Ubuntu, it didn't go so well... I'm hoping for better luck this time.

---

### Post by falkTX on 2008-08-02
There always the good "Super-Grub disk". It was useful for me several times.
It is used to repair the boot section

Check it out here:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by logos34 on 2008-08-02
If grub or the ubuntu installer does not detect vista, simply [add an entry manually to bottom of menu.lst.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu")  If grub is on the ubuntu disk, simply add an entry like in the 'mapping' link I gave you.

If you've opted for the first arrangement with grub (stage1 to be exact) on the mbr of the vista drive, and you reinstall the latter, overwriting grub in the process, simply restore grub via either the livecd (see link my signature) or Super Grub Disk.

---

### Post by CZStover on 2008-08-02
logos, thanks a million my friend!!  I'm rebuilding confidence as we speak (type).  It sounds like it would be preferable to install Ubuntu first then install vista... Can I set up two drives in "software raid" for Ubuntu and then make the two remaining drives use Matrix raid for vista?  Would this present any other potential problems above installing Ubuntu on just one disk?

---

### Post by logos34 on 2008-08-02
never tried a dual boot, dual raid setup, but here's some links on installing ubuntu on mirrored and striped raid arrays:

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)
[http://beginlinux.com/index.php/server_training/server-managment-topics/116-server-management/998-create-raid-on-ubuntu-804-part-1](http://beginlinux.com/index.php/server_training/server-managment-topics/116-server-management/998-create-raid-on-ubuntu-804-part-1)

---

