---
title: "windows 7/ubunto dual boot problem on z87 mother board (gryphon)"
date: 2013-07-13
forum: Installation &amp; Upgrades
---

### Post by wolf1o on 2013-07-13
I recently installed a win7 on my new z87 (asus gryhpon Motherboard) without any issue.

After I got it to work, I installed the latest linux (ubunto 13.04). I didn't mention but on purpose I installed the win7 on a separate ssd harddrive, and the linux from a different mechanical hd.

After I installed it, the system boots to the ununto grub menu, and I can boot to ubunto without any issue. but when I click on the windows 7 loader, it won't boot and it says "invalid EFI file path" and then i can click a key to go back to the menu.

Also, If I override the boot and choose the ssd, the system will boot to win7 successfully.

in addition, I had to reinstall the ubunto because of I didn't left a space on it for a partition I wanted for ntfs use. (media/data usage),so now my bios is showing two "uefi" ubunto devices of the mechanical drives - what does it means?
This is what I did when reinstalling the ubunto:
1. Unplugged the windows 7 ssd drive.
2. installed a "fresh" install (after formatting its partition) of ubunto on the connected mech. drive.
3. afterwards booted to ubunto (when win7 ssd is still disconnected) just to make sure it works.(works fine)
4. turned off the computer and connected the win7 ssd again.
5. Booted again to ubunto and did from the terminal the " apt-get update" and then "dist-upgrade" to update everything including the grub.
6. booted and got the grub menu, which allows me to boot to ubunto OK, but as mentioned the "windows 7 loader" won't work...


In any case, what can I do in order to fix the grub "efi file path" issue, so it will load the windows 7 properly from there?I'm quite loss and don't know how to proceed.
Is it possible that I should have installed the windows 7 from a UEFI usb loader, such as rufus?and install it in uefi/gpt mode?I read something about it now...I installed the win7 from a "standard" usb loader...and it works perfectly fine on its own..(even now when I bypass the grub menu...)


btw, after installing the ubunto, In the bios, I changed the "secure boot" option to "other os" instead of the windows uefi mode" i had there - was it a correct action to do?
I added the "EFI" error msg I get when trying to start the windows and also I edited the text in the grub menu to show what I have (I think!) under the windows loader option.


I'd really appreciate some help,thank!

---

### Post by wolf1o on 2013-07-14
anyone??

---

### Post by oldfred on 2013-07-14
Windows 7 probably installed in BIOS mode and Ubuntu in UEFI mode which makes it impossible to dual boot from grub menu. You have to go into UEFI/BIOS and turn on the mode to match install. UEFI and BIOS write system data differently and are not compatible.

You can use Boot-Repair to convert an Ubuntu install from UEFI to BIOS (or vice-versa) if installed with gpt partitioning as from gpt it boots with either mode. If MBR(msdos) partitioning you can only boot both systems in BIOS mode. Windows only boots from gpt partitioning in UEFI mode.

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

### Post by wolf1o on 2013-07-14
Solved!
In Short:
Installed the windows again from a rufus made installer (UEFI/GPT)
Reinstalled Linux.
Had to perform a "repair disk" which built the EFI entry. (No "windows 7 loader" now as I used to had in my old standard bios win7/linux machine)
Seems to works fine! Thanks!!!

---

### Post by wolf1o on 2013-07-14
Solved!
In Short:
Installed the windows again from a rufus made installer (UEFI/GPT)
Reinstalled Linux.
Had  to perform a "repair disk" which built the EFI entry. (No "windows 7  loader" now as I used to had in my old standard bios win7/linux machine)
Seems to works fine! Thanks!!!

---

