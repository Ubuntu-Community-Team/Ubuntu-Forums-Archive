---
title: "[ubuntu] Won't load after boot. I done goofed."
date: 2014-08-02
forum: Installation &amp; Upgrades
---

### Post by aidan5 on 2014-08-02
I managed to turn a 12 hour old Toshiba Satellite Z30-A into a paperweight.

I tried to dual boot the default win8 install with ubuntu, through partitioning the hard drive. Unfortunately, grub wouldn't load, even after using boot-repair. Instead, I would just boot to windows.
I then tried EasyBCD, and then both windows and ubuntu wouldn't load.

I then gave up on win8 (as I have a win7 copy somewhere I can install later), and tried to install ubuntu normally (wiping the hard disk). After the reboot, I get the message "Insert system disk in drive."
Another few runs of boot-repair only gave me these: [http://paste.ubuntu.com/7935425/](http://paste.ubuntu.com/7935425/) [http://paste.ubuntu.com/7935757/](http://paste.ubuntu.com/7935757/)

Booting through the live install, I can see that there's a ubuntu install on the hard disk, it's just not being loaded.


I've also tried installing win7 through a bootable USB to no avail, but I have no clue if the USB actually works.

I'm not too sure what's going on, but it seems like grub isn't even loading. It's 5am and I don't even know anymore.

Thanks in advance

---

### Post by ubfan1 on 2014-08-02
Looks like you have no bootloaders in your EFI partition.  Not sure how the Logical Vol you selected works, have no recent experience with those, but might have something to do with the lack of bootloaers (installer has to copy the bootloaders from the /usr/lib/grub/x86_64-efi-signed and /usr/lib/shim/shim.efi.signed) into the EFI partition's /EFI/ubuntu.  That should be what your nvram entry points to -- check it out with: sudo efibootmgr -v
Also, you will need a copy of grub.cfg in /EFI/ubuntu/grub.cfg .  Either the actual grub.cfg from /boot/grub or the 3 line stub the installer uses  which uses the configfile command to pull in the actual grub.cfg from /boot/grub.
As a fallback, I usually put in a copy of shim.efi (and the signed grubx64.efi) into /EFI/Boot (naming shim.efi to bootx64.efi).  Maybe you should try installing again without the logical volume business.

---

### Post by oldfred on 2014-08-02
I think only really knowledgeable users should be using LVM or RAID.
But now they include LVM as a default install and it is required if you want full drive encryption, but LVM is a full drive install erasing anything else like Windows and Windows recovery. Not intended for dual booting.

A Windows 7 DVD will only install in BIOS mode but can be converted to a flash drive and install in UEFI mode.
Windows only boots from gpt drives with UEFI and only with BIOS from MBR drives. And Windows 7 installer will not correctly convert a gpt partitioned drive to MBR, so fixparts is required.
Windows probably cannot see the full drive LVM as that is Linux so that is why it will not install.

       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

    
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by aidan5 on 2014-08-03
UPDATE: enabled CSM in UEFI, used rufus as per oldfred's instructions, and currently installing win7

---

### Post by aidan5 on 2014-08-03
UPDATE 2: Windows 7 is installed and running fine. Gonna try ubuntu now.

Also, [http://www.sevenforums.com/tutorials...ndows-7-a.html]("http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html") is the method I used for installing Windows

---

### Post by oldfred on 2014-08-03
If you have enable CSM/BIOS then be sure to boot Ubuntu in BIOS mode also. And install Ubuntu into logical partitions inside one extended partition.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

