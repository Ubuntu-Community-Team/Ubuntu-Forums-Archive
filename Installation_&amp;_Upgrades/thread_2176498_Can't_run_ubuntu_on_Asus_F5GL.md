---
title: "Can't run ubuntu on Asus F5GL"
date: 2013-09-24
forum: Installation &amp; Upgrades
---

### Post by Matej_imk on 2013-09-24
Good Afternoon,

I tried install Ubuntu 13.04 on my Asus F5GL win vista pre-installed (later updated to win7).
Live usb test went fine, so i decided to install it. I selected to install it along with win7, everything went fine, after installation was done it wrote that i should restart computer to start using Ubuntu, but after restart it didn't gave me option to choose if i want run win or Ubuntu and it just ran win. i want to ask, is able to fix it somehow or i will have to format all hdd to install it successfully? :-?

Sorry for my bad english

---

### Post by oldfred on 2013-09-27
Welcome to the forums.

Best to see details. Sometimes grub just does not install to MBR of hard drive and this can easily fix that if only that issue.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

