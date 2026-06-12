---
title: "Dual booting Win8 with Ubuntu 12.04 [Samsung NP550P5C]"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by simonr93 on 2013-05-09
Hi everyone, I've been practically bashing my head against a wall with this problem. I'm fairly new to Linux and fancied a change from Windows, especially after their horrible excuse of an OS that is Windows 8.

So, I downloaded the live CD and during the install I wasn't given an "install along side windows 8" option, I was only given the option to remove whatever was on there and just install Ubuntu (which I didn't want) and "something else". So I did that. I fist of all partitioned my HDD to 500GB for windows and 500GB for Ubuntu (if I liked Ubuntu I planned on giving it the full TB) then added the necessary partition things. "ext4 'mounting as' /boot"@485000mb  "swap @ 5000" and "Grub @ 10000"- I wasn't sure how much to give it, and everything installed as expected until I was asked to reboot.

I rebooted my computer and removed the disk as instructed, nothing happened so I rebooted again-- this time Win8 booted and no Grub menu came up. I then pressed and held shift while restarting windows at the login screen, apparently Ubuntu wasn't an option to boot, only DVD drive and Windows 8. I thought maybe I had not installed it or something, so I placed the Live CD in again and looked in the Home Folder, clicked on the partition I installed it on and boom, there are all the files for Ubuntu.

I don't know how/why my laptop isn't allowing me to boot from and installed version of Ubuntu.

Is this sort of thing common? Any help would be greatly appreciated. :)

Thanks,
Simon.

EDIT: Just to clarify, I can't use the full version of ubuntu that is installed on my HDD, only the Live CD version which doesn't allow me to save all my work etc. There is no option to boot Ubuntu, it just directly goes to Windows 8 without a grub menu.

Picture of files while running live CD: [http://imgur.com/a/kbfzS](http://imgur.com/a/kbfzS)

---

### Post by oldfred on 2013-05-09
I am not sure how you have installed? Best to see details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

You normally only need / (root) not a separate /boot partition. Often if dual booting with Windows a separate NTFS data partition is also a good idea.

---

### Post by simonr93 on 2013-05-09
[http://paste.ubuntu.com/5649662/](http://paste.ubuntu.com/5649662/) <-- this is my boot information.

---

### Post by oldfred on 2013-05-10
You have Windows in UEFI and Ubuntu in BIOS. Usually better to install Ubuntu in UEFI as that is the only way you can easily dual boot from grub menu. The only way you can boot is to go into UEFI, turn on UEFI mode and boot Windows. Does your Windows boot with secure boot on or with it off. Many only boot with it on.
And to boot Ubuntu you have to go into UEFI turn off UEFI and turn on BIOS/CSM/legacy mode to boot. 
Not an easy way to dual boot.

Boot repair will convert your BIOS install to UEFI, by uninstalling grub-pc  and installing grub-efi.

If you can boot Windows without secure boot then you do not have to have Boot-Repair install signed kernels and grub and rename files. But if you have one of those sytems that only boots with secure boot on you need signed versions of grub & kernel. Some also violate UEFI and only boot the Windows efi file. Boot-Repair can do a renaming to work around that issue.

       Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
It does this:
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 


 How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

---

