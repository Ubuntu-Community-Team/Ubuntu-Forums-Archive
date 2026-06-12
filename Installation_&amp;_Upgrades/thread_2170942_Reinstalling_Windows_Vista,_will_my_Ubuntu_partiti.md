---
title: "Reinstalling Windows Vista, will my Ubuntu partition be deleted?"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by Jonah_J._Jameson on 2013-08-28
Hey everyone,

                     I have Ubuntu 13.04 dual installed with Windows Vista. I wanted to reinstall my Windows C: drive, If i did would the Windows instilation override Ubuntu and delete it? If so, any solutions to solve my problem?

Thanks alot, J.J.J.

---

### Post by oldfred on 2013-08-28
It should just reinstall to the same NTFS partition as it currently is installed. That partition has to be NTFS with the boot flag.

Also anytime you change systems around be sure to have good backups.

But all installs write their boot loader to the MBR, so you will need your Ubuntu live installer or other Linux repairCD to reinstall the grub2 boot loader to the MBR.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by Jonah_J._Jameson on 2013-08-28
Alright, thanks alot man
ill let you know how it goes when i get around to it.
-J.J.J.

---

### Post by O2Blevel on 2013-08-31
I'm getting ready to do the same thing but I would also like to resize the windows partition. I'm thinking of deleting the windows partition and split in two, and then reinstalling vista to one of the new partitions. I will format it NTFS in gparted and I believe I can also use gparted to enable the boot flag. Does that sound feasible or is there a better way?

---

### Post by oldfred on 2013-08-31
Generally we suggest Windows for Windows things and Linux for Linux.
But repartitioning with gparted should work.
There are actually two NTFS versions, but it is the PBR - partition boot sector. The one for XP has a PBR that specifies to boot with ntldr. Vista/7/8 have a PBR that uses bootmgr. I think gparted only makes the XP version but the Windows installer should update it. If not you may have to reformat with the Windows installer or run chkdsk from Vista or later.
I once ran chkdsk on my XP from a Windows 7 repair flash drive. It actually worked better but converted PBR to boot with bootmgr. But Windows repair also has a way to write a XP compatible PBR.

---

