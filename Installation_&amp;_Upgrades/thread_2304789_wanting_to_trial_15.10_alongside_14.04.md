---
title: "wanting to trial 15.10 alongside 14.04"
date: 2015-11-29
forum: Installation &amp; Upgrades
---

### Post by Hodor on 2015-11-29
Hi,
I want to trial the above, both booting in uefi, 15.10 secure boot.
14.04 currently uefi boot but not secure boot.
I've booted into 15.10 with secure boot on.
From the 'try ubuntu', if I click 'install ubuntu', can I just go with 'install ubuntu 15.10 alongside 14.04' or do I need to do 'something else'?
The drive that has my windows installation is currently removed so I'm just ignoring that for the moment.

Thank you

---

### Post by oldfred on 2015-11-30
I would only use Something Else. Otherwise it resizes partitions on its own.
I have several 25GB partitions on two drives and use them for installs.

Do make a backup of your ESP - efi system partition. Grub only installs to sda and your new install will put its grub into the ESP as /EFI/ubuntu overwriting your existing EFI/ubuntu. 
But it turns out the only real difference is the /EFI/ubuntu/grub.cfg which is just 3 lines of configfile to find your grub.cfg in your install. You can just copy the old grub.cfg or manually edit it. I have had to do both. First time or two I manually edited it. Then made backups. Then made copies in /EFI as /EFI/trusty and /EFI/vivid & /EFI/wily. But UEFI will not directly boot them as grub is hard coded to find the grub.cfg in /EFI/ubuntu.

---

### Post by Bucky Ball on 2015-11-30
Where is the UEFI boot partition? If that is on the Windows drive that you have removed you are going to run into issues I would think as that is what is booting the current Ubuntu. The next install may create a UEFI boot partition on the Ubuntu drive as well. When you put the Win drive back in and boot you'll now have two UEFI partitions. Confusion may entail at this point, or possibly earlier.

Which drive is the UEFI boot partition on? The Win or the Ubuntu?

---

### Post by Hodor on 2015-11-30
Hi Bucky Ball, I booted without the windows drive in. I think the ubuntu uefi partition is on the drive that is currently in.  I think the windows drive has it's own uefi partition that knows nothing about ubuntu.  Grub 2 has seen the the windows boot loader (from booting while that drive was connected) but I never use grub to boot windows.  I chose my boot option in the uefi firmware. I *think* the firmware grabs info about boot loaders off the uefi partitions when it loads, but I've never really got to the bottom of that - I just use my current setup and I'm hoping it will continue, with the uefi firmware loading another boot loader option after installing 15.10, if it goes to plan.

---

### Post by oldfred on 2015-11-30
When you disconnect a drive, UEFI forgets that drive's UEFI entries.
You may have to cold boot several times as most UEFI will add entries. Or you may need to use efibootmgr in Ubuntu or live installer to add a new Windows UEFI boot entry.

Many of the efibootmgr instructions assume defaults of first drive or sda. But you can specify another drive when installing.

       This should create a new entry, if ESP is sda1, uses defaults:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
if ESP sda2, you have to specify drive & partition
sudo efibootmgr -c -d /dev/sda -p 2 -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"


 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

### Post by Hodor on 2015-11-30
Thanks oldfred, re the first post: I'll back up my ESP. For a manual installation following 'something else' I'll follow this: [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
re the second post: as I don't use grub to boot into windows, my plan at this stage is to just do the Ubuntu installation, ignore windows and when Ubuntu is running fine, reconnect the Windows drive and attempt to boot into windows via the uefi firmware.  (I think the firmwares pointers to the windows boot manager will be fine after I reconnect the Windows drive because I think the firmware grabs these off the Windows drive, I don't think it uses the Ubuntu drive for this.)  Thoughts?
Edit: when I upgraded Windows 8.1 to 10, I just removed my Ubuntu drive, reconnected it at the end and it all went fine.

---

### Post by Hodor on 2015-11-30
All went well - secure boot into 15.10 and now 14.04 as well.
Windows boots fine after plugging in the drive again.
Thanks again oldfred and Bucky Ball

---

### Post by Bucky Ball on 2015-11-30
Good news. Please see the first link in my signature and enjoy. :)

---

