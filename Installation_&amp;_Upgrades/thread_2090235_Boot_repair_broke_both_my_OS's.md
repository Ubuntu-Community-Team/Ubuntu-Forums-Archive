---
title: "Boot repair broke both my OS's"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by proudpedestrian on 2012-12-01
Hello, 

I recently got ubuntu 12.10 installed on my new uefi toshiba ultrabook along side windows 8.  I followed these instructions to get the installation working (had to get around intel SRT): 

[http://ubuntuforums.org/showthread.php?t=2020155#10](http://ubuntuforums.org/showthread.php?t=2020155#10)

Everything went okay with the installation but I could no longer boot into windows so i ran boot-repair (using the recommended repair).  This seemed to work for a hot second. I rebooted and grub loaded correctly so i booted up windows to test.  Everything worked, windows loaded, so i restarted again and went to boot ubuntu but after selecting ubuntu in grub it just hung.  I had to force turn off my laptop. Then when i restarted, grub no longer came up and it loaded the trouble shooting page for windows. (ubuntu and windows now fail to load).

What makes matters worse is that my usb boot disk of 12.10 will no longer boot either.  So i can't even get back into to boot repair.  I also don't have a CD drive so I can't burn the boot repair disk.  

Please help! my brand new laptop is essentially an $800 paperweight right now.

here is the output of the boot repair job: [http://paste.ubuntu.com/1402939/](http://paste.ubuntu.com/1402939/)

---

### Post by oldfred on 2012-12-01
You cannot have two efi partitions. Only your sda2 should be the efi or ESP  partition. The sda6 then cannot be an efi partition. 

> In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

    

Do you have secure boot on or off. If on that may be why it will not boot flash drive or anything else.

It looks like you tried a wubi install. It is my understanding that wubi will not work with gpt or UEFI installs.

---

### Post by proudpedestrian on 2012-12-01
> It looks like you tried a wubi install. It is my understanding that wubi will not work with gpt or UEFI installs.

I did not try to do a wubi isntall. 

> Do you have secure boot on or off. If on that may be why it will not boot flash drive or anything else.


I have tried to boot the usb (and everything else for that matter) with both secure boot enabled and disabled.  Same results both time.

I was unaware that you could only have one efi partition. if i can get back into the boot disk i can fix this. any ideas?

---

### Post by oldfred on 2012-12-01
You can use gparted or download and use gdisk which is the fdisk for gpt partitioned drives. gdisk is in the Ubuntu repository or you can download the newest version from the rodbooks site. It is also on many Linux repair CDs.

Also these ways:
       You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot off
sudo parted /dev/sda set 6 boot off


GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

The UEFI menu should give you the option to boot either ubuntu or Windows. And then it remember that for future reboots. Best to boot ubuntu/grub as it will allow you to also boot Windows, but if ubuntu is not working the try Windows directly.

---

### Post by proudpedestrian on 2012-12-05
Turns out my usb drive somehow became corrupted after the install.  I created a new boot stick and then used it to delete the extra efi partition.  After running boot-repair again everything worked great! Thanks so much

---

### Post by YannBuntu on 2012-12-05
Good job!
For our information, please could you run Boot-Repair --> "Create BootInfo"  (not "Recommended Repair"), and tell us the new URL that will appear?
(this will show you current situation, without changing your boot)

---

