---
title: "Getting rid of GRUB after an uninstall, bootrec commands not working."
date: 2017-08-02
forum: Installation &amp; Upgrades
---

### Post by litepegasus on 2017-08-02
I have a dell xps 13 9350, with a 512 GB m.2 PCLe 9Toshiba SSD. I uninstalled 16.04 LTS and still had the grub bootloader. What I did:

1) Went into the Windows partition manager, tried to clean and format everything I could. I had no out-of-the-ordinary partitions. 
2) Booted into windows recovery, and tried to diagnose boot problems- no errors found
3) From windows recovery, I used the command prompt to run "bootrec/fixmbr"  and "bootrec/fixboot", both completed instantly, no solution

Then I realized that maybe it was a bios problem, because of my 512 gb RAID ssd. I went into the bios, turned off both "ACHI" and "Raid" settings, and repeated the command prompt step. Same outcome, same results. 

How can I remove GRUB, short of a full system reset? Will a full system reset even solve the GRUB problem?

---

### Post by yancek on 2017-08-02
You neglected to indicate which release of windows you are using making it very difficult to help.  Newer versions of windows ( 8, 10) use UEFI and GPT partitioning.  Older systems use MBR but you can do MBR with newer windows.  We would first need to know which windows and whether it is MBR or UEFI.

There are a number of things which could be causing your problems.  The first thing you did wrong was to go in and format/delete the Ubuntu partitions from windows.  The commands you post for repairing the MBR should have been run first and then tested on a reboot.  If you are using an MBR system I would have expected the commands you ran in windows to work and don't know why they would not.  I'm unfamiliar with RAID so don't know if that matters.  If you can post some info on your partition structure, someone may be able to help.  If you don't get any responses here, you might try a windows forum to get help booting windows.

---

### Post by oldfred on 2017-08-02
Your system is a newer UEFI system. If Windows is installed in UEFI boot mode, you should be able to just set it to first in UEFI boot order.

But with UEFI, you have to remove the /EFI/ubuntu folder in the ESP partition (FAT32), which Windows does not normally mount. Be sure not to delete the /EFI/microsoft folder.
And remove the ubuntu entries from the UEFI. UEFI has NVRAM which saves boot menu entries.

 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 


        Uninstall Ubuntu from menu, Really UEFI boot menu 
[URL="http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi"]http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi
[/URL]
 How To Remove Ubuntu From A Computer Dual Booting With Windows 10
[http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html](http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html)
Delete /EFI/ubuntu folder from Windows
[http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/) 

[URL="http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi"]
[/URL]

---

### Post by litepegasus on 2017-08-02
I have a windows 10 machine. I added details about my ssd because in order to use Ubuntu, I usually have to turn off Raid mode, or else get stuck on the Ubuntu loading screen. My MBR partition looks normal, with one 500 MB EFI system partition, but I probably am not seeing everything because I've previously needed to turn off Raid mode to see Ubuntu partitions- and Windows 10 won't run without it.

I'll try to reinstall ubuntu then run the commands, both in the windows cmd and in Ubuntu's terminal.
Thanks Everyone!

---

### Post by oldfred on 2017-08-02
With your Dell you add the AHCI drivers in Windows before changing UEFI from RAID to AHCI.
 XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI

[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)

More general UEFI install instructions in link in my signature.

Now current versions of Ubuntu have this or newer kernel.
 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers) 

Similar model Dell

 Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)

---

### Post by litepegasus on 2017-08-02
I tried reinstalling ubuntu and running commands- no dice. 
oldfred, I've updated my BIOS and still have the same issues. Seems like the links you've posted have the person booting into windows safe mode, but nothing about running both windows and Ubuntu at the same time in their fullest capacities.

---

### Post by oldfred on 2017-08-02
Do you have latest UEFI from Dell?
Have you updated firmware for SSD?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by litepegasus on 2017-08-03
yes and yes. 

However, I ended up going into my windows command prompt, navigating to within the UEFI boot partition, and deleting the "ubuntu" volume. Here's a video I loosely followed:
[https://www.youtube.com/watch?v=rxYSzxXawjU](https://www.youtube.com/watch?v=rxYSzxXawjU)
now I've remove the bootloader! Thanks everyone for helping.

---

