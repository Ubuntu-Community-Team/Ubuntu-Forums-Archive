---
title: "Ubuntu 12.10 / Windows 7 dualboot: Unknown filesystem, grub rescue"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by twistle on 2013-01-30
Help! D:
 
I have a Ubuntu 12.10 and Windows 7 dualboot installed on my Asus Zenbook. I wanted to remove Ubuntu, so I thought I could follow this guide to restore the Windows boot loader [http://www.howtogeek.com/howto/33433/restore-the-windows-boot-loader-after-an-ubuntu-update/](http://www.howtogeek.com/howto/33433/restore-the-windows-boot-loader-after-an-ubuntu-update/) and remove the linux partition after that. I also have the Asus recovery partition, so I booted into that to see whether the Asus recovery wizard had an repair option. Well, it didn't, the only option was to recover Windows to the entire hd. So I canceled the wizard, but after this I was greeted with "error: unknown filesystem" and the grub rescue prompt. 
 
I'm scared of messing things up further, what should I do to either get back to my dualboot or create a windows-only-boot?
Would booting a Live USB and restoring the Windows bootloader with syslinux or mbr work? ([http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/comment-page-1/](http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/comment-page-1/))
I'm a newbie, so I'm not sure about the sda part though. The windows partition is sda1, does that mean I should replace dev/sda in "[FONT=Courier New]sudo install-mbr -i n -p D -t 0 /dev/sda" with dev/sda1?

[/FONT]Any help will be greatly appreciated!

---

### Post by oldfred on 2013-01-30
NO.

Almost never install a boot loader to a partition and never to a NTFS partition (PBR) as that has to have NTFS partition boot code and info which is different than MBR boot code.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
You should be able to use a Windows RepairCD and run auto repairs 3 times or the fixMBR command. Whichever partition is boot needs the Windows boot flag or set as active partition with Windows repair. Windows 7 usually has a 100MB boot/repair partition as sda1 or sda2 and then the main install.

You can also run this:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
       An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

    
Boot-Repair install syslinux boot loader. If you have liveCD/DVD/Flash from Linux you can also install lilo's boot loader to the MBR (not full lilo which also has boot code in a PBR).

       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by twistle on 2013-02-01
Thank you very much!

The Boot-Repair tool worked like a charm!

I should have mentioned that I don't have a CD-drive. So I ended up using EasyBCD and the Windows Disk Manager, as described here: [http://askubuntu.com/a/110679/127726](http://askubuntu.com/a/110679/127726)

---

