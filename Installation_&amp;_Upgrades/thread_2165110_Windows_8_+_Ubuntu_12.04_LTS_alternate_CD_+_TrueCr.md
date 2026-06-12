---
title: "Windows 8 + Ubuntu 12.04 LTS alternate CD + TrueCrypt"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by johndoe2 on 2013-08-03
Hi,

because of safety reasons I've installed:

1.) Windows 8 with full encryption by using TrueCrypt

2.) Ubuntu 12.04 LTS with home folder encryption, I've used alternate CD but installing grub failed, I dont know why so I've finished installing Ubuntu without grub

And now I have TrueCrypt bootloader on master boot record but I dont know what to do know.

I've google a lot but the is no simple solution on my problem.


I was reading this tutorial [http://utcomsoc.ece.utexas.edu/index.php/knowledge-base/28-it-tips-and-tricks/51-dual-booting-windows-7-with-ubuntu-12-04lts-with-truecrypt](http://utcomsoc.ece.utexas.edu/index.php/knowledge-base/28-it-tips-and-tricks/51-dual-booting-windows-7-with-ubuntu-12-04lts-with-truecrypt) except that grub installation failed so I finished without installing grub. I thought I can install grub later but now I dont know how.

Please help me.

---

### Post by oldfred on 2013-08-04
You have to install grub2's boot loader to the Ubuntu partition's PBR or partition boot sector. Since that is not really large enough you have to force the install or use Boot-Repair. It has to convert to blocklists or hard coded addresses to find the rest of the grub code in the Ubuntu partition. If an update to grub files moves files on drive, they will not be found and you have to reinstall grub to PBR, so have Ubuntu repairCD or flash drive handy.

       Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

Do not know if Boot-Repair will automatically ask for pass phrase when trying to open encrypted files or not. You may have to mount first.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

