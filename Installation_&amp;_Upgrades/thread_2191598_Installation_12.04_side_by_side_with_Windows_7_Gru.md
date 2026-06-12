---
title: "Installation 12.04 side by side with Windows 7 Grub Problem"
date: 2013-12-03
forum: Installation &amp; Upgrades
---

### Post by nd.mashiah on 2013-12-03
Hi, i am a new Ubuntu user,
i have installed Ubuntu 12.04LTS on my X1 Carbon while windows 7 is installed on other partition.
after installing and restart i get "Invalid arch independent ELF"
I have try few fixes but it doesnt work.
i am sure there are alot of you who have worked it out.

Thank you for helping a linux newbe :D
David.

---

### Post by oldfred on 2013-12-03
error: invalid arch independent ELF magic

 Often version of grub in MBR is not same as install. 
Use same version to reinstall or chroot and fully uninstall & reinstall grub.

You should try Boot-Repair but may have to run the full uninstall and reinstall of grub.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

