---
title: "grub2 uefi problems"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by garfoil on 2013-03-12
new computer with uefi bios--formatted drive removing windows 8--installed linux mint 14--grub 2 installed on linux-mint---installed ubuntu-12.04 next
but it didnt load grub--installed grub-customizer on ubuntu 12.04 and made changes----saved changes but didnt take--boot menu stays with linux mint

---

### Post by oldfred on 2013-03-12
Did you install both with BIOS mode not UEFI mode. Is drive still gpt or MBR(msdos).

May be best to see details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

