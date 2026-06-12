---
title: "Windows 7 doesn't show up in the boot menu after upgrade to 12.04.4 LTS"
date: 2014-03-04
forum: Installation &amp; Upgrades
---

### Post by mks3 on 2014-03-04
Hi 

   I just upgraded my ubuntu to 12.04.4 LTS and can not find the original Windows 7 OS on boot up.  I used boot-repair and the output is saved at 
[http://paste.ubuntu.com/7034313/](http://paste.ubuntu.com/7034313/)

I would appreciate any help in what to do next!

Thanks.

Manoj

---

### Post by oldfred on 2014-03-04
Did you leave Windows hibernated? Or is has some issue as even Boot-Repair did not mount the NTFS partitions. So then the os-prober could not mount it and see the Windows boot files.

I would install a Windows type boot loader to sda and try directly booting Windows. You can use Boot-Repair to install a generic Windows boot loader using Advanced and install syslinux boot loader to sda. If it still does not see Windows I am not sure you can force it.

Or you can use your Windows repair CD or Flash drive to install the Windows MBR with fixMBR command. If running auto repairs you have to run those 3 times.

Or you can install the lilo boot loader which also is another Windows like boot loader. You only want the MBR part of Lilo as it also is another boot loader with additional boot code.

       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

If then you can mount the NTFS partitions, run this in Ubuntu:
       sudo update-grub

---

