---
title: "Ubuntu Booting Problem"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by chnandakishore on 2013-04-04
Hi all. I have installed ubuntu 12.04 on external HDD, and while installation, i have selected external device for boot loader installation.
After installation is completed, while booting, it loaded grub and showed the options to load linux, and windows.
But, after i have disconnected the External drive and restarted the system, the Grub is loading now, and it is showing an error of Device not found(the external device which i have installed).Now, i have connected the drive, but still the same error is coming up. Now, i have formatted the partition in which windows is installed,and installed Ubuntu on the internal drive, by
creating an extended drive, and creating 2 sub partitions,I did this because, i already have 4 primary partitions, so deleted one main partition, and made it extended and then divided it into 2 sub partitions, 1 primary and 1 logical(ubuntu is installed in this),Is it right method, do like this???.
 Now, when i have restarted the system. again the old grub is loading, and showing the same error of device"e5XXXXX-..XXX" not found..

What should i do now? Even, if i have formatted the windows partition and installing the windows, while restarting, the same device not found error is coming. Not able to install Windows, and also if installed ubuntu, not able to load it.. Please help me..

Installing Ubuntu on logical drive is correct??

---

### Post by oldfred on 2013-04-04
Only one primary partition can be converted to an extended partition and then you can have many logical partitions inside the extended.

While you say you installed grub2's boot loader to the MBR of the external drive, it sounds like it may have installed to the internal drive. And the rest of grub to boot is on the external drive.

Just to see where you are at now.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

