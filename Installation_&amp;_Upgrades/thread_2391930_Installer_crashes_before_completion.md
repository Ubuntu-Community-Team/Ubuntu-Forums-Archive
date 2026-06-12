---
title: "Installer crashes before completion"
date: 2018-05-14
forum: Installation &amp; Upgrades
---

### Post by oldtraveler2 on 2018-05-14
Using a USB thumb drive to install all is well until near the end there is a message about being unable to install grub.  Then comes a message saying the installation has failed.

My pc has a ssd drive plus two hard drives.  Win 10 is on the ssd and on the hdds besides data files there are various other partitions including Linux Mint.  This is a new pc so my previous grub is not on this pc.  If I can  install ubuntu to one of the available partitions it should install grub. 

Would the problem be that I am not using the correct partition for the grub boot loader?

[ATTACH=CONFIG]279695[/ATTACH]

---

### Post by yancek on 2018-05-14
Two of your hard drives (including the smaller one with windows) are GPT and the smaller windows drive has an EFI partition.  The third drive is a Legacy/MBR install with your various Linux systems on it.  Mixing a Legacy/MBR install with a UEFI/GPT install will always cause problems.  Is the message you get any more specific than 'the installation failed'.  Did you boot and try to install Ubuntu EFI or Legacy.  Before we get into too many questions, I would suggest you read the Ubuntu documentation at the lin below on dual booting windows 10/Ubuntu UEFI. If you tried a Legacy default install, you would have to install Grub from Ubuntu to the MBR of that same drive.  You could also have selected to install Grub to the / partition on which you installed Ubuntu and rebooted whichever OS you had in the MBR and run update-grub.  Need to know if there was a  more specific error. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you still have questions and haven't resolved the situation after reading through the link, get boot repair and run it with the Create BootInfo Summary option and post the link here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldtraveler2 on 2018-05-14
When I booted to the USB installer I went to the bios and selected the bootable USB which was noted to be UEFI.

As you suggested I ran the installation again and set the partition on which I wish to install unbuntu for the boot loader.  

During install I received this message:
The 'grub-efi-amd64 signed' package failed to install in /target/.  Without the GRUB boot loader the installed system will not boot.

Then came the message:
installer crashed

We're sorry ........

---

### Post by oldtraveler2 on 2018-05-15
I have tried installing ubuntu 18.04 in sdb6 several times.  Each time I selected a different partition upon which to have the grub boot loader installed.  Each time the installer installed most files, but when it got to installing grub I got the error message noted above.

I haven't tried the Boot Repair yet for two reasons.  One is that I did run that utility three days ago with no joy and further it messed up my Wjindows 10 boot so that I had to go to tech support to get that working again. Secondly, I believe, (tell me if I am wrong) that Boot Repair can only help IF there is a grub loader somewhere on the pc.  THERE IS NO GRUB BOOT LOADER located anywhere on this pc.  I would appreciate assistance in getting a grub boot loader installed on this pc.

I tried one more time after creating a small FAT32 partition on disk 2 which I used as the location for the grub boot loader.  Still no joy.

SOLVED
By changing disk 2 to GPT and then creating a small partition as EFI system which I used as the location for the grub boot loader the installation completed.

---

