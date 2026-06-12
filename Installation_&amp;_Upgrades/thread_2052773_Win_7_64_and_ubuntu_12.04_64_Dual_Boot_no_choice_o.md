---
title: "Win 7 64 and ubuntu 12.04 64 Dual Boot no choice of OS on Boot"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by JasRenkai on 2012-09-03
Hello!
 
I had to add an Ubuntu install to my current laptop. I have successfully installed both Windows 7 and Ubuntu. 
 
I do not get a an option when my computer boots up to select which OS I would like to boot into. I have to enter the BIOS everytime and change the bootloader. I have deleted and reinstalled Ubuntu twice already (since it is pretty fast and painless). 
 
I feel like it has something to do with this laptop being an ASUS UEFI system, but I can not find any threads that mirror this exact problem, or concise steps to fixing it. Or it could be that I am not completely deleting Ubuntu correctly. It's not a HUGE deal just annoying right now while I'm switching between the two 5 or 6 times a day.
 
Any advice or thread links would be greatly appreciated!!

---

### Post by oldfred on 2012-09-04
Welcome to the forums.

Run this and post link to BootInfo it creates. 

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

If you have a UEFI/BIOS system. Both Windows & Ubuntu have to be either BIOS/MBR or UEFI/gpt. If first partition is efi and you have gpt partitioning then Ubuntu also needs to be in UEFI mode.

 Yann has updated Boot repair for converting a grub-pc (grub2 in BIOS mode) to grub-efi (grub2 in efi mode). Actually install is otherwise the same.

---

### Post by JasRenkai on 2012-09-04
I performed the Boot Repair as advised. It did generate a repair file but it could not connect to the internet within the little portable OS to create a URL. It did save it to the root.
 
Now when the system boots up it does come to a purple screen with 7 options. The top option will boot in Ubuntu, the bottom option will boot in Windows.
 
Is this menu Grub's bootloader? Will it be overwritten whenever windows updaes?

---

### Post by darkod on 2012-09-04
Yes, that is the grub boot menu.

It will not be overwritten when windows updates. It will be overwritten if you reinstall windows or install another version of windows. This is because windows installer doesn't offer the option to leave the current bootloader on the MBR alone. It overwrites it. But restoring grub in that case is very easy.

So, if by windows updates you mean the regular security updates, that doesn't remove grub.

---

### Post by JasRenkai on 2012-09-04
Sweet Thanks!

---

