---
title: "Windows 8 not booting from Grub"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by websterandy42 on 2013-11-06
I have a Lenovo Y500 with Win 8 Preinstalled, i went through the ubuntu instilation and did the special options because it did not give me the option to dualboot. Sooo i split my main partition in half and installed ubuntu on that. when it restarted it went strait to win 8 so i restarted with the same ubuntu live cd and ran boot repair. this got me to a grub menue with only ubuntu. so i went in and updated grub with [sudo update-grub], this kinda worked exept that now i have 3 options in the menu: 
Ubuntu, 
Win on sda, 
and Win on sdb;
 but only ubuntu works. ( i have two hardrives sda is 16 gigs and sdb is 1 Terra) when i select Win Sda it goes to a purple screen and Sdb acts like it is running something but never does.

My partitions
SDA
[System reserved]          Unalocated           [linux-swap]
SDB
[ ntfs (Windows)] [ext4 (Linux)]

and my boot report thing
[http://paste.ubuntu.com/6372322/](http://paste.ubuntu.com/6372322/)

Sorry about spelling
Any advice on how to get windows working?

---

### Post by oldfred on 2013-11-06
Is Windows 8 hibernated or has fast boot on?
I would install the Windows boot loader to the MBR of sda and leave grub on sdb. Then with one time boot key you can manually boot Windows if grub is not working or if you leave fast boot on or it needs chkdsk. Grub will only boot a working Windows.
You can use Boot-Repair. Under advance unchoose the auto update, but check the update MBR. Then under boot choose Windows and sda to install a Windows boot loader. Or use your Windows 8 repairCD to fix Windows.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by websterandy42 on 2013-11-06
That gets me to an error screen where I am missing win 32 files. And does not let me do anything as far as repairing with instillation media. All it does is flicker the screen a little. Do you know of anything else or a very specific guide to dual booting on my computer, I'm willing to wipe all the drives and start over at this point.

---

### Post by websterandy42 on 2013-11-06
I still have access to gparted and boot repair through the Ubuntu live CD Im just locked out of my installed Ubuntu now.

---

### Post by oldfred on 2013-11-06
You can install lilo boot loader to sda. It works just like Windows.

 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

Then see if from BIOS or one time boot key you can boot sda. You could also try lilo in sdb, in case that Windows BCD is more correct.

If you want to reinstall, my suggestion would be to just put / on the 16GB. Having Windows boot & swap on it does not add anything.
My root is 11GB including /home but I have all data in data partitions on my hard drive. My /home is 2GB or my / without /home is 9GB with lots of apps. Unless installing lots of games or other large apps you should be able to fit  the entire / into the 16GB. You may want to periodically houseclean but it will make booting Ubuntu and loading system very fast.
Then you can have Windows just on hard drive, and have a shared NTFS data partition and /home also on hard drive.

---

### Post by websterandy42 on 2013-11-06
What order would you suggest installing them in? And would grub even be needed or could you boot to either directly using f12?

---

### Post by oldfred on 2013-11-06
If you have a Windows boot loader in sda and grub in sdb, then you can boot either from f12 or BIOS. Windows should boot from grub menu, but with Windows 8 fast boot must be off or users are having issues.

---

